# Native资源显式移交场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta静态Native能力以[ANI简介](../ani/ani-introduction.md)中介绍的ANI为主。若业务需要“转移所有权”的语义，可以使用Native资源句柄加显式移交协议：宿主线程创建Native资源后，将句柄传给[taskpool (启动任务池)](../reference/apis-arkts/arkts-sta-taskpool.md)任务，并在宿主线程侧标记该句柄已移交，后续不再访问该资源。

本文以Native集合为例，说明如何通过ArkTS侧所有权状态和C++侧资源表实现资源显式移交。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 声明Native资源接口

使用native方法声明C++侧资源管理接口。以下为ArkTS-Sta示例。

```ts
// ArkTS-Sta示例
// NativeSet.ets
export class NativeSet {
  native create(): long;
  native store(handle: long, value: int): void;
  native size(handle: long): int;
  native release(handle: long): void;
}
```

## 封装显式移交句柄

NativeHandoffHandle只在ArkTS侧维护所有权状态。调用detachForTask()后，宿主线程不应再通过该对象访问Native资源。

```ts
// ArkTS-Sta示例
// NativeHandoffHandle.ets
export class NativeHandoffHandle {
  private handle: long = 0;
  private detached: boolean = false;

  constructor(handle: long) {
    this.handle = handle;
  }

  public getHandle(): long {
    if (this.detached) {
      throw new Error("native resource has been transferred");
    }
    return this.handle;
  }

  public detachForTask(): long {
    this.detached = true;
    return this.handle;
  }
}
```

## 在TaskPool任务中使用已移交资源

TaskPool任务只接收Native资源句柄，并通过Native接口访问资源。任务完成后可按业务要求释放资源，或将句柄返回给宿主线程重新建立新的所有权协议。

```ts
// ArkTS-Sta示例
// NativeHandoffTask.ets
import { NativeSet } from './NativeSet'

export function writeHandedOffResource(handle: long): int {
  let nativeSet: NativeSet = new NativeSet();
  nativeSet.store(handle, 1);
  nativeSet.store(handle, 2);
  nativeSet.store(handle, 3);
  return nativeSet.size(handle);
}
```

## Native侧实现资源表

Native侧可以使用句柄表管理资源，并使用C++锁保护多线程访问。以下代码仅展示关键实现，工程中还需要配置CMakeLists.txt并在应用侧加载Native库。

```cpp
// ani_init.cpp
#include "ani/ani.h"
#include <array>
#include <atomic>
#include <cstdint>
#include <mutex>
#include <unordered_map>
#include <unordered_set>

struct NativeSetData {
    std::unordered_set<int32_t> values;
};

static std::mutex g_resourceMutex;
static std::atomic<int64_t> g_nextHandle {1};
static std::unordered_map<int64_t, NativeSetData> g_resources;

static ani_long Create([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object)
{
    int64_t handle = g_nextHandle.fetch_add(1);
    std::lock_guard<std::mutex> lock(g_resourceMutex);
    g_resources.emplace(handle, NativeSetData {});
    return static_cast<ani_long>(handle);
}

static void Store([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object,
    ani_long handle, ani_int value)
{
    std::lock_guard<std::mutex> lock(g_resourceMutex);
    auto iter = g_resources.find(static_cast<int64_t>(handle));
    if (iter != g_resources.end()) {
        iter->second.values.insert(static_cast<int32_t>(value));
    }
}

static ani_int Size([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object, ani_long handle)
{
    std::lock_guard<std::mutex> lock(g_resourceMutex);
    auto iter = g_resources.find(static_cast<int64_t>(handle));
    if (iter == g_resources.end()) {
        return 0;
    }
    return static_cast<ani_int>(iter->second.values.size());
}

static void Release([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object, ani_long handle)
{
    std::lock_guard<std::mutex> lock(g_resourceMutex);
    g_resources.erase(static_cast<int64_t>(handle));
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
        ani_native_function {"size", "l:i", reinterpret_cast<void *>(Size)},
        ani_native_function {"release", "l:", reinterpret_cast<void *>(Release)},
    };
    return env->Class_BindNativeMethods(cls, methods.data(), methods.size());
}

ANI_EXPORT ani_status ANI_Constructor(ani_vm *vm, uint32_t *result)
{
    if (BindNativeMethods(vm, "entry.src.main.ets.pages.NativeSet.NativeSet") != ANI_OK) {
        return ANI_ERROR;
    }
    *result = ANI_VERSION_1;
    return ANI_OK;
}
```

## 在页面中移交资源

宿主线程创建Native资源，并在提交TaskPool任务前显式移交句柄。移交后不要再通过原NativeHandoffHandle访问该资源。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { NativeSet } from './NativeSet'
import { NativeHandoffHandle } from './NativeHandoffHandle'
import { writeHandedOffResource } from './NativeHandoffTask'

@Entry
@Component
struct Index {
  @State message: string = "ready";
  private nativeSet: NativeSet = new NativeSet();
  private owner: NativeHandoffHandle | undefined = undefined;

  private createResource(): void {
    loadLibrary("entry");
    this.owner = new NativeHandoffHandle(this.nativeSet.create());
    this.message = "resource created";
    console.info("resource created"); // resource created
  }

  private async transferToTask(): Promise<void> {
    if (this.owner === undefined) {
      console.info("native resource is not created"); // native resource is not created
      return;
    }

    let handle: long = this.owner.detachForTask();
    let size: int = (await taskpool.execute(writeHandedOffResource, handle)) as int;
    this.message = "task set size: " + size;
    console.info("task set size: " + size); // task set size: 3
    this.nativeSet.release(handle);
    this.owner = undefined;
  }

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)
      Button("create")
        .onClick((e: ClickEvent) => {
          this.createResource();
        })
      Button("transfer")
        .onClick((e: ClickEvent) => {
          this.transferToTask();
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- 需要转移语义时，应使用句柄、状态位或所有权字段显式描述资源归属，并在代码中阻止移交后的宿主线程继续访问。
- Native资源表必须处理资源释放，避免句柄泄漏。异常路径和任务取消路径也应释放或回收资源。
- 多线程访问同一Native资源时，C++侧必须使用std::mutex、std::atomic等机制保护共享状态。
- loadLibrary应在首次调用Native方法前执行。示例类名entry.src.main.ets.pages.NativeSet.NativeSet需要与工程中实际文件路径和类名一致。
