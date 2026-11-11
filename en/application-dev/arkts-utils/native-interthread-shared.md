---
kits: ["ArkTS / Ark Programming Language"]
description: "Introduces the development method for C++ inter-thread data sharing scenarios: supports invoking ArkTS capabilities on C++ threads, and operating Sendable shared objects between C++ threads, applicable to data interaction scenarios in hybrid development of Native multithreading and ArkTS."
keywords: [C++ thread, inter-thread data sharing, Sendable shared object, Native thread, cross-language invocation, ArkTS capability invocation, hybrid development, multithreading]
doctype: guide
status: active
---

# C++ Inter-Thread Data Sharing
<!--Kit: ArkTS-->
<!--Subsystem: CommonLibrary-->
<!--Owner: @huanghello-->
<!--Designer: @weng-changcheng-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @k1ngqaquuu-->
<!-- md-trans-meta sourceCommit=f8431cb42cf0d545a37a384860003cd8449b0b43 translatedAt=2026-11-06T10:41:01.455Z pushedAt=2026-11-09T09:09:08.285Z nl=1 -->

When performing multithreaded computations at the C++ layer, an ArkTS execution environment must be created for each C++ thread to enable direct API calls. This prevents non-UI main threads from waiting for API results from the UI main thread when executing callbacks. Additionally, Sendable objects must be shared and manipulated across C++ threads.

To support these scenarios, C++ threads need the capability to create and invoke ArkTS, as well as share and manipulate Sendable objects across threads.


## Calling ArkTS APIs on C++ Threads

For details about how to use Node-API to create an ArkTS runtime environment and call ArkTS APIs on C++ threads, see [Creating an ArkTS Runtime Environment Using Node-API](../napi/use-napi-ark-runtime.md).

The core code snippet is as follows:

ArkTS file definition

<!-- @[arkts_define_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/NativeInterthreadShared/entry/src/main/ets/pages/SendableObjTest.ets) -->

``` TypeScript
@Sendable
export class SendableObjTest {
  private value: number = 1024;
  static newSendable(): SendableObjTest {
    return new SendableObjTest();
  }
  public getValue(): number {
    return this.value;
  }
}
```

Native implementation to load ArkTS modules

<!-- @[native_load_arkts_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/NativeInterthreadShared/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include <thread>

#include "napi/native_api.h"
// Used to compare and confirm the value of the obtained sendable object.
const int SENDABLE_VALUE = 1024;

static void* g_serializationData = nullptr;
static void* CreateEnvAndSendSendable(void*)
{
    // 1. Create the ArkTS runtime environment.
    napi_env env = nullptr;
    napi_status ret = napi_create_ark_runtime(&env);
    if (ret != napi_ok) {
        std::abort();
    }
    // 2. Load the custom module, assuming that SendableObjTest provides the newSendable function for creating Sendable objects.
    napi_value test = nullptr;
    ret = napi_load_module_with_info(
        env, "entry/src/main/ets/pages/SendableObjTest", "com.example.myapplication/entry", &test);
    if (ret != napi_ok) {
        std::abort();
    }
    napi_value sendableObjTest = nullptr;
    ret = napi_get_named_property(env, test, "SendableObjTest", &sendableObjTest);
    if (ret != napi_ok) {
        std::abort();
    }
    // 3. Use newSendable in ArkTS, assuming that the newSendable function in sendableObjTest returns a Sendable object.
    napi_value newSendable = nullptr;
    ret = napi_get_named_property(env, sendableObjTest, "newSendable", &newSendable);
    if (ret != napi_ok) {
        std::abort();
    }
    // 4. Call the newSendable function to return the newly created Sendable object and store it in result.
    napi_value result = nullptr;
    ret = napi_call_function(env, sendableObjTest, newSendable, 0, nullptr, &result);
    if (ret != napi_ok) {
        std::abort();
    }
    // 5. Serialize the Sendable object.
    napi_value undefined;
    napi_get_undefined(env, &undefined);
    ret = napi_serialize(env, result, undefined, undefined, &g_serializationData);
    if (ret != napi_ok) {
        std::abort();
    }
    napi_destroy_ark_runtime(&env);
    return nullptr;
}
```

The process consists of four steps: creating an execution environment, loading modules, searching for and calling functions (or directly creating Sendable objects through Node-API), and finally destroying the execution environment. For details about how to load modules, see [Loading a Module Using Node-API](../napi/use-napi-load-module-with-info.md). For details about how to search for and call functions and more Node-API capabilities, see [Node-API](../reference/native-lib/napi.md).

## Manipulating Sendable Objects Across C++ Threads

After implementing the capabilities to call ArkTS APIs from C++, serialize and deserialize objects for cross-thread transfer. **napi_value** is not thread-safe and therefore cannot be directly operated or shared across threads.

The following code example demonstrates how to serialize and deserialize objects. Since Sendable objects are passed by reference, serialization does not create an additional copy of the data but directly passes the object reference to the deserializing thread. This makes serialization and deserialization more efficient than non-Sendable objects.

ArkTS file definition

<!-- @[arkts_define_obj](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/NativeInterthreadShared/entry/src/main/ets/pages/SendableObjTest.ets) -->

``` TypeScript
@Sendable
export class SendableObjTest {
  private value: number = 1024;
  static newSendable(): SendableObjTest {
    return new SendableObjTest();
  }
  public getValue(): number {
    return this.value;
  }
}
```

Native implementation for serialization and deserialization of Sendable objects

<!-- @[native_deserialize_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/NativeInterthreadShared/entry/src/main/cpp/napi_init.cpp) -->

``` C++
#include <thread>

#include "napi/native_api.h"
// Used to compare and confirm the value of the obtained sendable object's value
const int SENDABLE_VALUE = 1024;

static void* g_serializationData = nullptr;
static void* CreateEnvAndSendSendable(void*)
{
    // 1. Create the ArkTS runtime environment.
    napi_env env = nullptr;
    napi_status ret = napi_create_ark_runtime(&env);
    if (ret != napi_ok) {
        std::abort();
    }
    // 2. Load the custom module, assuming that SendableObjTest provides the newSendable function for creating Sendable objects.
    napi_value test = nullptr;
    ret = napi_load_module_with_info(
        env, "entry/src/main/ets/pages/SendableObjTest", "com.example.myapplication/entry", &test);
    if (ret != napi_ok) {
        std::abort();
    }
    napi_value sendableObjTest = nullptr;
    ret = napi_get_named_property(env, test, "SendableObjTest", &sendableObjTest);
    if (ret != napi_ok) {
        std::abort();
    }
    // 3. Use newSendable in ArkTS, assuming that the newSendable function in sendableObjTest returns a Sendable object.
    napi_value newSendable = nullptr;
    ret = napi_get_named_property(env, sendableObjTest, "newSendable", &newSendable);
    if (ret != napi_ok) {
        std::abort();
    }
    // 4. Call the newSendable function to return the newly created Sendable object and store it in result.
    napi_value result = nullptr;
    ret = napi_call_function(env, sendableObjTest, newSendable, 0, nullptr, &result);
    if (ret != napi_ok) {
        std::abort();
    }
    // 5. Serialize the Sendable object.
    napi_value undefined;
    napi_get_undefined(env, &undefined);
    ret = napi_serialize(env, result, undefined, undefined, &g_serializationData);
    if (ret != napi_ok) {
        std::abort();
    }
    napi_destroy_ark_runtime(&env);
    return nullptr;
}

static void* CreateEnvAndReceiveSendable(void*)
{
    // 1. Create the ArkTS runtime environment.
    napi_env env = nullptr;
    napi_status ret = napi_create_ark_runtime(&env);
    if (ret != napi_ok) {
        std::abort();
    }
    // 2. Deserialize the Sendable object and store it in result, which can then be manipulated via Node-API.
    napi_value result = nullptr;
    ret = napi_deserialize(env, g_serializationData, &result);
    if (ret != napi_ok) {
        std::abort();
    }
    // 3. Delete the serialization data.
    ret = napi_delete_serialization_data(env, g_serializationData);
    if (ret != napi_ok) {
        std::abort();
    }
    // 4. Obtain the getValue method from the result object
    napi_value getValueFunc = nullptr;
    ret = napi_get_named_property(env, result, "getValue", &getValueFunc);
    if (ret != napi_ok) {
        std::abort();
    }
    // 5. Call the getValue method with result as this, and store the return value in valueResult
    napi_value valueResult = nullptr;
    ret = napi_call_function(env, result, getValueFunc, 0, nullptr, &valueResult);
    if (ret != napi_ok) {
        std::abort();
    }
    // 6. Confirm that valueResult is of the number type
    napi_valuetype valuetype0;
    napi_typeof(env, valueResult, &valuetype0);
    if (valuetype0 != napi_number) {
        std::abort();
    }
    // 7. 1024 is used to determine whether the result returned by ArkTS is correct
    int value0;
    napi_get_value_int32(env, valueResult, &value0);
    if (value0 != SENDABLE_VALUE) {
        std::abort();
    }
    napi_destroy_ark_runtime(&env);
    return nullptr;
}

static napi_value TestSendSendable([[maybe_unused]] napi_env env, [[maybe_unused]] napi_callback_info info)
{
    // The UI main thread creates the t1 thread
    std::thread t1(CreateEnvAndSendSendable, nullptr);
    t1.join();
    // The UI main thread creates the t2 thread
    std::thread t2(CreateEnvAndReceiveSendable, nullptr);
    t2.join();
    return nullptr;
}

EXTERN_C_START
static napi_value Init(napi_env env, napi_value exports)
{
    napi_property_descriptor desc[] = { { "testSendSendable", nullptr, TestSendSendable, nullptr, nullptr, nullptr,
        napi_default, nullptr } };
    napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
    return exports;
}
EXTERN_C_END

static napi_module demoModule = {
    .nm_version = 1,
    .nm_flags = 0,
    .nm_filename = nullptr,
    .nm_register_func = Init,
    .nm_modname = "entry",
    .nm_priv = ((void*)0),
    .reserved = { 0 },
};

extern "C" __attribute__((constructor)) void RegisterEntryModule(void)
{
    napi_module_register(&demoModule);
}
```

<!-- @[native_deserialize_sendable](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/NativeInterthreadShared/entry/src/main/cpp/types/libentry/Index.d.ts) -->

``` TypeScript
export const testSendSendable: () => void;
```

UI main thread invocation

<!-- @[main_thread_init_call](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/ArkTsConcurrent/ApplicationMultithreadingDevelopment/NativeInterthreadShared/entry/src/main/ets/pages/Index.ets) -->

``` TypeScript
import { hilog } from '@kit.PerformanceAnalysisKit';
import testNapi from 'libentry.so';
import { SendableObjTest } from './SendableObjTest'

@Entry
@Component
struct Index {
  @State message: string = 'Hello World';

  build() {
    Row() {
      Column() {
        Text(this.message)
          .fontSize(50)
          .fontWeight(FontWeight.Bold)
          .onClick(() => {
            SendableObjTest.newSendable()
            hilog.info(0x0000, 'testTag', 'Test send Sendable begin');
            testNapi.testSendSendable();
            hilog.info(0x0000, 'testTag', 'Test send Sendable end');
            this.message = 'success';
          })
      }
      .width('100%')
    }
    .height('100%')
  }
}
```

The logic implementation of the entire process is as follows:

1. The UI main thread creates a C++ child thread t1, creates the ArkTS runtime environment and loads the ArkTS module, creates a Sendable object and saves it to result, and then serializes the Sendable object referenced by result into the global serialization data serializationData.

2. After these processes are complete, the UI main thread creates a C++ child thread t2 and creates an ArkTS runtime environment in this new thread. It then deserializes the Sendable object created by thread t1 from serializationData through the deserialization interface and saves it to result, thereby implementing cross-C++-thread transfer of the Sendable object. After deserialization is complete, the serialized data must be destroyed to avoid memory leaks.

   > **NOTE**
   >
   > The object being manipulated must comply with the rules of Sendable objects. For details, see [Usage Rules and Constraints for Sendable](sendable-constraints.md).