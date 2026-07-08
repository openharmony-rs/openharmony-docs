# C++线程间数据共享场景 (ArkTS-Sta)
<!--Kit: ArkTS-->
<!--Subsystem: Utils-->
<!--Owner: @MofengMa-->
<!--Designer: @MofengMa-->
<!--Tester: @zsw_zhushiwei-->
<!--Adviser: @ge-yafang-->

ArkTS-Sta应用可以通过Native方法调用C++能力。与动态ArkTS中通过Node-API创建运行环境、序列化Sendable对象的方式不同，ArkTS-Sta静态场景使用[ANI简介](../ani/ani-introduction.md)中介绍的ANI（ArkTS Native Interface）绑定native方法，并通过ani_vm在线程中附加ArkTS运行环境。

C++线程之间共享数据时，应优先使用C++侧的std::atomic、std::mutex等同步机制保护共享状态；如果C++线程需要回调ArkTS静态方法，需要先将当前C++线程附加到ArkTS VM，获取该线程可用的ani_env，调用完成后再分离线程。

> **说明：**
>
> - 本文仅适用于ArkTS-Sta。

## 定义Native类

以下为ArkTS-Sta示例。使用native声明由C++实现的方法，并提供一个静态方法供C++线程附加后回调。

```ts
// ArkTS-Sta示例
// NativeShare.ets
export class NativeShare {
  native add(arg1: int, arg2: int): int;
  native startNativeThread(): int;

  public static onNativeThreadReady(): void {
    console.info("native thread callback"); // native thread callback
  }
}
```

## 绑定Native方法并启动C++线程

在ANI_Constructor中查找ArkTS类，并通过Class_BindNativeMethods绑定Native实例方法。C++线程需要调用ArkTS接口时，不能复用宿主线程传入的ani_env；应先通过env->GetVM获取ani_vm，在线程函数中调用AttachCurrentThread得到当前线程的ani_env。

```cpp
// ani_init.cpp
#include "ani/ani.h"
#include <array>
#include <atomic>
#include <cstdint>
#include <iostream>
#include <thread>

static std::atomic<int32_t> g_sharedValue {0};

static ani_int Add([[maybe_unused]] ani_env *env, [[maybe_unused]] ani_object object,
    ani_int arg1, ani_int arg2)
{
    return arg1 + arg2;
}

static ani_int StartNativeThread(ani_env *env, [[maybe_unused]] ani_object object)
{
    ani_vm *vm = nullptr;
    if (env->GetVM(&vm) != ANI_OK) {
        return -1;
    }

    ani_status workerStatus = ANI_OK;
    std::thread worker([vm, &workerStatus]() {
        ani_env *workerEnv = nullptr;
        ani_option interopEnabled = {"--interop=enable", nullptr};
        ani_options aniArgs {1, &interopEnabled};

        workerStatus = vm->AttachCurrentThread(&aniArgs, ANI_VERSION_1, &workerEnv);
        if (workerStatus != ANI_OK) {
            std::cout << "testTag : AttachCurrentThread failed" << std::endl;
            return;
        }

        g_sharedValue.fetch_add(1, std::memory_order_relaxed);

        ani_class cls {};
        workerStatus = workerEnv->FindClass("entry.src.main.ets.pages.NativeShare.NativeShare", &cls);
        if (workerStatus == ANI_OK) {
            workerStatus = workerEnv->Class_CallStaticMethodByName_Void(
                cls, "onNativeThreadReady", ":");
        }

        ani_status detachStatus = vm->DetachCurrentThread();
        if (workerStatus == ANI_OK) {
            workerStatus = detachStatus;
        }
    });

    worker.join();
    if (workerStatus != ANI_OK) {
        return -1;
    }
    return static_cast<ani_int>(g_sharedValue.load(std::memory_order_relaxed));
}

static ani_status BindNativeMethods(ani_vm *vm, const char *className)
{
    ani_env *env = nullptr;
    if (vm->GetEnv(ANI_VERSION_1, &env) != ANI_OK) {
        std::cerr << "Unsupported ANI_VERSION_1" << std::endl;
        return ANI_ERROR;
    }

    ani_class cls {};
    if (env->FindClass(className, &cls) != ANI_OK) {
        std::cerr << "Not found '" << className << "'" << std::endl;
        return ANI_ERROR;
    }

    std::array methods = {
        ani_native_function {"add", "ii:i", reinterpret_cast<void *>(Add)},
        ani_native_function {"startNativeThread", ":i", reinterpret_cast<void *>(StartNativeThread)},
    };

    if (env->Class_BindNativeMethods(cls, methods.data(), methods.size()) != ANI_OK) {
        std::cerr << "Cannot bind native methods to '" << className << "'" << std::endl;
        return ANI_ERROR;
    }
    return ANI_OK;
}

ANI_EXPORT ani_status ANI_Constructor(ani_vm *vm, uint32_t *result)
{
    if (BindNativeMethods(vm, "entry.src.main.ets.pages.NativeShare.NativeShare") != ANI_OK) {
        return ANI_ERROR;
    }
    *result = ANI_VERSION_1;
    return ANI_OK;
}
```

上述示例中，g_sharedValue是C++侧线程间共享状态，使用std::atomic保证并发读写安全。C++工作线程通过AttachCurrentThread获取workerEnv后，重新查找NativeShare类并调用静态方法onNativeThreadReady。

示例中的类名entry.src.main.ets.pages.NativeShare.NativeShare对应entry/src/main/ets/pages/NativeShare.ets文件中的NativeShare类。如果Native类放在其他目录或使用其他类名，需要同步修改FindClass和ANI_Constructor中的类名。

如果共享状态是多个字段组成的复合数据，不能只依赖普通变量读写。可以使用std::mutex保护读写临界区。

```cpp
#include <mutex>
#include <string>

struct NativeRecord {
    int32_t id;
    std::string name;
};

static std::mutex g_recordMutex;
static NativeRecord g_record {0, ""};

static void UpdateRecord(int32_t id, const std::string &name)
{
    std::lock_guard<std::mutex> lock(g_recordMutex);
    g_record.id = id;
    g_record.name = name;
}

static NativeRecord SnapshotRecord()
{
    std::lock_guard<std::mutex> lock(g_recordMutex);
    return g_record;
}
```

## 配置Native构建

Native代码需要以共享库方式编译，并在应用侧加载。可以在entry/src/main/cpp/CMakeLists.txt中配置Native库。

```cmake
cmake_minimum_required(VERSION 3.5.0)
project(NativeShare)

set(NATIVERENDER_ROOT_PATH ${CMAKE_CURRENT_SOURCE_DIR})
set(CMAKE_CXX_STANDARD 17)

if(DEFINED PACKAGE_FIND_FILE)
    include(${PACKAGE_FIND_FILE})
endif()

include_directories(${NATIVERENDER_ROOT_PATH}
                    ${NATIVERENDER_ROOT_PATH}/include)

add_library(entry SHARED ani_init.cpp)
```

同时在模块的build-profile.json5中配置CMake路径。

```json
{
  "apiType": "stageMode",
  "buildOption": {
    "externalNativeOptions": {
      "path": "./src/main/cpp/CMakeLists.txt"
    }
  }
}
```

## 在ArkUI页面中调用Native方法

调用Native方法前需要加载Native库。以下示例在按钮事件中调用loadLibrary("entry")加载libentry.so，再调用Native方法启动C++线程。

```ts
// ArkTS-Sta示例
// Index.ets
import { Entry, Text, Column, Component, Button, ClickEvent } from '@ohos.arkui.component'
import { State } from '@ohos.arkui.stateManagement'
import { NativeShare } from './NativeShare'

@Entry
@Component
struct Index {
  @State message: string = "ready";
  private nativeShare: NativeShare = new NativeShare();

  build() {
    Column(undefined) {
      Text(this.message).fontSize(20)

      Button("load native")
        .onClick((e: ClickEvent) => {
          try {
            loadLibrary("entry");
            this.message = "native loaded";
            console.info("load native success"); // load native success
          } catch (error) {
            this.message = "load failed";
            console.info("load native failed"); // load native failed
          }
        })

      Button("start native thread")
        .onClick((e: ClickEvent) => {
          let value: int = this.nativeShare.startNativeThread();
          this.message = "shared value: " + value;
          console.info("shared value: " + value); // shared value: 1
        })
    }
    .height('100%')
    .width('100%')
  }
}
```

## 使用建议

- 静态ArkTS中Native方法建议通过ANI绑定。动态ArkTS文档中的Node-API运行环境创建、Sendable序列化等写法不适合作为ArkTS-Sta静态示例直接迁移。
- C++线程访问ArkTS能力前必须附加到ArkTS VM。一个线程只应在成功AttachCurrentThread后执行一次对应的DetachCurrentThread，重复附加或重复分离会返回错误。
- ani_env与当前附加线程相关，不应直接跨C++线程复用。需要在线程中调用ArkTS类或方法时，建议在当前线程获取到的ani_env上重新查找类和方法。
- C++线程共享数据应使用C++同步机制保护。只读数据可以直接读取；可变计数、标志位等轻量状态可以使用std::atomic；复合结构应使用std::mutex等锁保护。
- 如果同一份状态同时被ArkTS线程和C++线程访问，需要明确状态归属和同步边界。ArkTS侧可结合锁、原子能力或并发容器保护共享对象；C++侧仍需遵守C++内存模型。
- 不建议从C++工作线程直接操作ArkUI组件或UI状态。需要更新界面时，应将结果返回宿主线程，再在宿主线程更新ArkUI状态。
