# Native共享资源多线程操作场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta对象默认按共享引用在线程间传递。若业务需要让宿主线程和[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)任务共同访问Native大对象，可以使用[ANI简介](../ani/ani-introduction.md)中介绍的ANI暴露Native资源接口，并通过Native句柄访问同一份C++资源。共享资源的线程安全由C++侧锁或原子能力保证。

本文以共享Native集合为例，说明如何在ArkTS-Sta中通过Native句柄访问同一份C++资源，并在Native侧保护共享状态。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 声明共享Native资源接口

使用native方法声明Native资源的创建、写入和读取接口。资源通过long类型句柄在ArkTS和C++之间传递。

```ts
// ArkTS-Sta示例
// NativeSharedSet.ets
export class NativeSharedSet {
  native create(): long;
  native store(handle: long, value: int): void;
  native erase(handle: long, value: int): void;
  native size(handle: long): int;
  native release(handle: long): void;
}
```

## 在TaskPool任务中操作共享Native资源

TaskPool任务接收Native资源句柄，并调用Native接口修改资源。宿主线程持有同一个句柄，因此任务返回后可以继续读取同一份Native数据。

```ts
// ArkTS-Sta示例
// NativeSharedTask.ets
import { NativeSharedSet } from './NativeSharedSet'

export function storeInTask(handle: long, start: int): int {
  let nativeSet: NativeSharedSet = new NativeSharedSet();
  nativeSet.store(handle, start);
  nativeSet.store(handle, start + 1);
  nativeSet.store(handle, start + 2);
  return nativeSet.size(handle);
}
```

## Native侧保护共享状态

共享Native资源需要在C++侧自行保证线程安全。以下示例使用全局资源表和std::mutex保护std::unordered_set读写。

```cpp
// ani_init.cpp
#include "ani/ani.h"
#include <array>
#include <atomic>
#include <cstdint>
#include <mutex>
#include <unordered_map>
#include <unordered_set>

struct SharedSetData {
    std::unordered_set<int32_t> values;
};

static std::mutex g_sharedMutex;
static std::atomic<int64_t> g_nextHandle {1};
static std::unordered_map<int64_t, SharedSetData> g_sharedSets;

static ani_long Create([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object)
{
    int64_t handle = g_nextHandle.fetch_add(1);
    std::lock_guard<std::mutex> lock(g_sharedMutex);
    g_sharedSets.emplace(handle, SharedSetData {});
    return static_cast<ani_long>(handle);
}

static void Store([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object,
    ani_long handle, ani_int value)
{
    std::lock_guard<std::mutex> lock(g_sharedMutex);
    auto iter = g_sharedSets.find(static_cast<int64_t>(handle));
    if (iter != g_sharedSets.end()) {
        iter->second.values.insert(static_cast<int32_t>(value));
    }
}

static void Erase([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object,
    ani_long handle, ani_int value)
{
    std::lock_guard<std::mutex> lock(g_sharedMutex);
    auto iter = g_sharedSets.find(static_cast<int64_t>(handle));
    if (iter != g_sharedSets.end()) {
        iter->second.values.erase(static_cast<int32_t>(value));
    }
}

static ani_int Size([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object, ani_long handle)
{
    std::lock_guard<std::mutex> lock(g_sharedMutex);
    auto iter = g_sharedSets.find(static_cast<int64_t>(handle));
    if (iter == g_sharedSets.end()) {
        return 0;
    }
    return static_cast<ani_int>(iter->second.values.size());
}

static void Release([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object, ani_long handle)
{
    std::lock_guard<std::mutex> lock(g_sharedMutex);
    g_sharedSets.erase(static_cast<int64_t>(handle));
}

static ani_status BindNativeMethods(ani_vm *vm, const char *className)
{
    ani_env *env = nullptr;
    if (vm->GetEnv(ANI_VERSION_1, &env) != ANI_OK) {
        return ANI_ERROR;
    }

    ani_class cls {};
    if (env->FindClass(className, &cls) != ANI_OK) {
        return ANI_ERROR;
    }

    std::array methods = {
        ani_native_function {"create", ":l", reinterpret_cast<void *>(Create)},
        ani_native_function {"store", "li:", reinterpret_cast<void *>(Store)},
        ani_native_function {"erase", "li:", reinterpret_cast<void *>(Erase)},
        ani_native_function {"size", "l:i", reinterpret_cast<void *>(Size)},
        ani_native_function {"release", "l:", reinterpret_cast<void *>(Release)},
    };
    return env->Class_BindNativeMethods(cls, methods.data(), methods.size());
}

ANI_EXPORT ani_status ANI_Constructor(ani_vm *vm, uint32_t *result)
{
    if (BindNativeMethods(vm, "entry.src.main.ets.pages.NativeSharedSet.NativeSharedSet") != ANI_OK) {
        return ANI_ERROR;
    }
    *result = ANI_VERSION_1;
    return ANI_OK;
}
```

## 宿主线程和TaskPool共享访问

宿主线程创建Native资源并写入数据，TaskPool任务继续写入同一资源。任务完成后，宿主线程读取到的是同一份C++资源的最新状态。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { NativeSharedSet } from './NativeSharedSet'
import { storeInTask } from './NativeSharedTask'

@Entry
@Component
struct Index {
  @State message: string = "ready";
  private nativeSet: NativeSharedSet = new NativeSharedSet();
  private handle: long = 0;

  private createResource(): void {
    loadLibrary("entry");
    this.handle = this.nativeSet.create();
    this.nativeSet.store(this.handle, 100);
    this.message = "host size: " + this.nativeSet.size(this.handle);
    console.info(this.message); // host size: 1
  }

  private async runTask(): Promise<void> {
    if (this.handle == 0) {
      console.info("native resource is not created"); // native resource is not created
      return;
    }

    let taskSize: int = (await taskpool.execute(storeInTask, this.handle, 200)) as int;
    let hostSize: int = this.nativeSet.size(this.handle);
    this.message = "task size: " + taskSize + ", host size: " + hostSize;
    console.info(this.message); // task size: 4, host size: 4
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)
      Button("create")
        .onClick((e: ClickEvent) => {
          this.createResource();
        })
      Button("run task")
        .onClick((e: ClickEvent) => {
          this.runTask();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- ArkTS-Sta中共享Native资源时，建议使用ANI绑定native方法，并通过Native句柄访问C++侧资源。
- 共享Native资源时，应把线程安全放在Native实现中处理。ArkTS侧传递句柄并不自动保证C++对象访问安全。
- 需要共享访问时，宿主线程和TaskPool任务可以持有同一Native句柄；需要所有权转移时，应使用显式移交协议，避免多个线程继续访问同一资源。
- Native资源生命周期应由业务明确管理。资源不再使用时调用释放接口，避免长期保存句柄导致Native内存泄漏。
- loadLibrary应在首次调用Native方法前执行。示例类名entry.src.main.ets.pages.NativeSharedSet.NativeSharedSet需要与工程中实际文件路径和类名一致。
