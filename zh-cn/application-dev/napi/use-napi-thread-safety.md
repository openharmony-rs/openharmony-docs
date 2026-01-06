# 使用Node-API接口进行线程安全开发
<!--Kit: NDK-->
<!--Subsystem: arkcompiler-->
<!--Owner: @xliu-huanwei; @shilei123; @huanghello-->
<!--Designer: @shilei123-->
<!--Tester: @kirl75; @zsw_zhushiwei-->
<!--Adviser: @fang-jinxu-->


## 场景介绍

[napi_create_threadsafe_function](../reference/native-lib/napi.md#napi_create_threadsafe_function)是Node-API接口之一，用于创建一个线程安全的JavaScript函数。该函数主要用于在多个线程之间共享和调用，避免竞争条件和死锁。包含以下场景：


- 异步计算：若需执行耗时的计算或IO操作，可创建线程安全的函数，在另一线程中完成计算或IO操作，避免阻塞主线程，提升程序响应速度。

- 数据共享：若多个线程需访问同一份数据，可以创建一个线程安全的函数，避免数据进行读写操作时发生竞争条件或死锁等问题。

- 多线程编程：若需要进行多线程编程，可以创建一个线程安全的函数，确保多个线程之间的通信和同步操作正确。


## 使用示例

1. 定义线程安全函数在Native入口。

   <!-- @[napi_thread_safety_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/cpp/thread_safety.cpp) -->
   ```c++
   #include "napi/native_api.h"
   #include "hilog/log.h"
   #include <future>

   struct CallbackData {
       napi_threadsafe_function tsfn;
       napi_async_work work;
   };

   static napi_value StartThread(napi_env env, napi_callback_info info)
   {
       size_t argc = 1;
       napi_value jsCb = nullptr;
       CallbackData *callbackData = new CallbackData(); // 异步任务完成时释放
       napi_get_cb_info(env, info, &argc, &jsCb, nullptr, nullptr);

       // 创建一个线程安全函数
       napi_value resourceName = nullptr;
       napi_create_string_utf8(env, "Thread-safe Function Demo", NAPI_AUTO_LENGTH, &resourceName);
       napi_create_threadsafe_function(env, jsCb, nullptr, resourceName, 0, 1, nullptr, nullptr,
           nullptr, CallJs, &callbackData->tsfn);

       // 创建一个异步任务
       // ExecuteWork会执行在一个由libuv创建的非JS线程上，此处使用napi_create_async_work是为了模拟在非JS线程场景使用napi_call_threadsafe_function接口向JS线程提交任务
       napi_create_async_work(env, nullptr, resourceName, ExecuteWork, WorkComplete, callbackData,
           &callbackData->work);

       // 将异步任务加入到异步队列中
       napi_queue_async_work(env, callbackData->work);
       return nullptr;
   }
   ```

2. 模块注册。
   ```c++
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           {"startThread", nullptr, StartThread, nullptr, nullptr, nullptr, napi_default, nullptr}
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END

   static napi_module demoModule = {
       .nm_version = 1,
       .nm_flags = 0,
       .nm_filename = nullptr,
       .nm_register_func = Init,
       .nm_modname = "entry1",
       .nm_priv = ((void *)0),
       .reserved = {0},
   };

   extern "C" __attribute__((constructor)) void RegisterEntryModule(void) { napi_module_register(&demoModule); }
   ```

3. ArkTS侧示例代码

   <!-- @[napi_thread_safety_dts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/cpp/types/libentry1/Index.d.ts) -->
   ``` ts
   // 接口对应的.d.ts描述
   export const startThread: (callback: () => Promise<string>) => void;
   ```

   导入头文件
   ``` ts
   import nativeModule from 'libentry1.so';
   ```
   
   <!-- @[napi_thread_safety_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/ets/pages/Index.ets) -->
   ``` ts
   // ArkTS侧调用接口
   import nativeModule from 'libentry.so'; // 通过import的方式，引入Native能力

   let callback = (): Promise<string> => {
     return new Promise((resolve) => {
       setTimeout(() => {
         resolve("string from promise");
       }, 5000);
     });
   }
   nativeModule.startThread(callback);
   ```

## 子线程交互场景介绍

- napi_threadsafe_function在主线程和子线程使用并无差异，下面是子线程的使用示例。

### 基于[Worker](../../application-dev/arkts-utils/worker-introduction.md)实现的C++子线程与ArkTS子线程交互场景

1. 配置worker。

   ``` json5
   "buildOption": {
     "sourceOption": {
       "workers": [
         "./src/main/ets/worker/worker.ets"
        ]
     },
   }
   ```

2. 在Native入口定义线程安全函数并创建子线程。

   <!-- @[napi_call_threadsafe_function_cpp](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/cpp/thread_safety.cpp) -->

3. 模块注册。

   ``` c++
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           {"startWithCallback", nullptr, StartThread, nullptr, nullptr, nullptr, napi_default, nullptr}
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END

   static napi_module demoModule = {
       .nm_version = 1,
       .nm_flags = 0,
       .nm_filename = nullptr,
       .nm_register_func = Init,
       .nm_modname = "entry1",
       .nm_priv = ((void *)0),
       .reserved = {0},
   };

   extern "C" __attribute__((constructor)) void RegisterEntryModule(void) { napi_module_register(&demoModule); }
   ```

4. Worker线程示例代码。

   <!-- @[napi_call_threadsafe_function_worker](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/ets/worker/worker.ets) -->

5. ArkTS侧示例代码。

   <!-- @[napi_call_threadsafe_function_dts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/cpp/types/libentry1/Index.d.ts) -->

   导入头文件
   ``` ts
   import nativeModule from 'libentry1.so';
   import { worker } from '@kit.ArkTS';
   ```

   <!-- @[napi_call_threadsafe_function_worker_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/ets/pages/Index.ets) -->

### 基于[Taskpool](../../application-dev/arkts-utils/taskpool-introduction.md)实现的C++子线程与ArkTS子线程交互场景

1. native侧实现代码以及模块注册与“基于Worker实现的C++子线程与ArkTS子线程交互场景”一致，可直接复用。

2. ArkTS侧示例代码。

   ``` ts
   import nativeModule from 'libentry1.so';
   import { taskpool } from '@kit.ArkTS';

   @Concurrent
   function nativeCall(input : string): void {
     console.info('Taskpool thread received:%s', input);
     nativeModule.startWithCallback('Hello', (result: string) => {
       console.info('[Taskpool] Got from native:', result);
     });
   }

   async function testTaskpool() : Promise<void> {
     try {
       const task = new taskpool.Task(nativeCall, 'Start');
       await taskpool.execute(task);
     } catch (e) {
       console.error(`Taskpool execute error: ${e}`);
     }
   }
   ```

   <!-- @[napi_call_threadsafe_function_taskpool_ets](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/ArkTS/NodeAPI/NodeAPIClassicUseCases/NodeAPIApplicationScenario/entry/src/main/ets/pages/Index.ets) -->