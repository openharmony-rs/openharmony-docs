# Transient Task (C/C++)

<!--Kit: Background Tasks Kit-->
<!--Subsystem: ResourceSchedule-->
<!--Owner: @cheng-shichang-->
<!--Designer: @zhouben25-->
<!--Tester: @leetestnady-->
<!--Adviser: @Brilliantry_Rui-->

## When to Use

An application is suspended after it runs in the background for a short period of time. If the application needs to execute a short-time task in the background, for example, saving the status, it can request a transient task to extend the running time in the background.

## Available APIs

The following table lists the common APIs. For details, see [API Reference](../reference/apis-backgroundtasks-kit/capi-transient-task-api-h.md#functions).


| Name| Description|
| -------- | -------- |
| [int32_t OH_BackgroundTaskManager_RequestSuspendDelay(const char *reason, TransientTask_Callback callback, TransientTask_DelaySuspendInfo *info)](../reference/apis-backgroundtasks-kit/capi-transient-task-api-h.md#oh_backgroundtaskmanager_requestsuspenddelay)  | Requests a transient task.|
| [int32_t OH_BackgroundTaskManager_GetRemainingDelayTime(int32_t requestId, int32_t *delayTime)](../reference/apis-backgroundtasks-kit/capi-transient-task-api-h.md#oh_backgroundtaskmanager_getremainingdelaytime) | Obtains the remaining time of a transient task.|
| [int32_t OH_BackgroundTaskManager_CancelSuspendDelay(int32_t requestId)](../reference/apis-backgroundtasks-kit/capi-transient-task-api-h.md#oh_backgroundtaskmanager_cancelsuspenddelay) | Cancels a transient task.|
| [int32_t OH_BackgroundTaskManager_GetTransientTaskInfo(TransientTask_TransientTaskInfo  *transientTaskInfo)](../reference/apis-backgroundtasks-kit/capi-transient-task-api-h.md#oh_backgroundtaskmanager_gettransienttaskinfo) | Obtains all information about a transient task, including the remaining quota of the current day.|

## How to Develop

### Encapsulating the Functions and Registering Modules in the napi_init.cpp File

1. Encapsulate the functions.

   <!-- @[encapsulation_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/NativeTransientTask/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   #include "napi/native_api.h"
   #include "transient_task/transient_task_api.h"

   TransientTask_DelaySuspendInfo delaySuspendInfo;
   const int32_t TransientTask_TIMER = 3;
   static void Callback(void)
   {
       // The transient task is about to end. The service cancels the transient task here.
       OH_BackgroundTaskManager_CancelSuspendDelay(delaySuspendInfo.requestId);
   }

   // Request a transient task.
   static napi_value RequestSuspendDelay(napi_env env, napi_callback_info info)
   {
       napi_value result;
       int32_t res = OH_BackgroundTaskManager_RequestSuspendDelay("test", Callback, &delaySuspendInfo);
       if (res == 0) {
           napi_create_int32(env, delaySuspendInfo.requestId, &result);
       } else {
           napi_create_int32(env, -1, &result);
       }
       return result;
   }

   // Obtain the remaining time.
   static napi_value GetRemainingDelayTime(napi_env env, napi_callback_info info)
   {
       napi_value result;
       int32_t delayTime = 0;
       int32_t res = OH_BackgroundTaskManager_GetRemainingDelayTime(delaySuspendInfo.requestId, &delayTime);
       if (res == 0) {
           napi_create_int32(env, delayTime, &result);
       } else {
           napi_create_int32(env, -1, &result);
       }
       return result;
   }

   // Cancel the transient task.
   static napi_value CancelSuspendDelay(napi_env env, napi_callback_info info)
   {
       napi_value result;
       int32_t res = OH_BackgroundTaskManager_CancelSuspendDelay(delaySuspendInfo.requestId);
       napi_create_int32(env, res, &result);
       return result;
   }

   // Obtain all transient task information.
   TransientTask_TransientTaskInfo transientTaskInfo;

   static napi_value GetTransientTaskInfo(napi_env env, napi_callback_info info)
   {
       napi_value result;
       napi_create_object(env, &result);
       int32_t res = OH_BackgroundTaskManager_GetTransientTaskInfo(&transientTaskInfo);
       napi_value napiRemainingQuota = nullptr;
       // The data is successfully obtained. The data is formatted and returned to the API.
       if (res == 0) {
           napi_create_int32(env, transientTaskInfo.remainingQuota, &napiRemainingQuota);
           napi_set_named_property(env, result, "remainingQuota", napiRemainingQuota); // Format the total quota of the current day.
   
           napi_value info {nullptr};
           napi_create_array(env, &info);
           uint32_t count = 0;
           // Format all requested transient task information.
           for (int index = 0; index < TransientTask_TIMER; index++) {
               if (transientTaskInfo.transientTasks[index].requestId == 0) {
                   continue;
               }
            
               napi_value napiWork = nullptr;
               napi_create_object(env, &napiWork);
   
               napi_value napiRequestId = nullptr;
               napi_create_int32(env, transientTaskInfo.transientTasks[index].requestId, &napiRequestId);
               napi_set_named_property(env, napiWork, "requestId", napiRequestId);
   
               napi_value napiActualDelayTime = nullptr;
               napi_create_int32(env, transientTaskInfo.transientTasks[index].actualDelayTime, &napiActualDelayTime);
               napi_set_named_property(env, napiWork, "actualDelayTime", napiActualDelayTime);
   
               napi_set_element(env, info, count, napiWork);
               count++;
           }
           napi_set_named_property(env, result, "transientTasks", info);
       } else {
           napi_create_int32(env, 0, &napiRemainingQuota);
           napi_set_named_property(env, result, "remainingQuota", napiRemainingQuota);
           napi_value info {nullptr};
           napi_create_array(env, &info);
           napi_set_named_property(env, result, "transientTasks", info);
       }
       return result;
   }
   ```

2. Register the functions.

   <!-- @[registration_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/NativeTransientTask/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   EXTERN_C_START
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           {"RequestSuspendDelay", nullptr, RequestSuspendDelay, nullptr, nullptr, nullptr, napi_default, nullptr},
           {"GetRemainingDelayTime", nullptr, GetRemainingDelayTime, nullptr, nullptr, nullptr, napi_default, nullptr},
           {"CancelSuspendDelay", nullptr, CancelSuspendDelay, nullptr, nullptr, nullptr, napi_default, nullptr},
           {"GetTransientTaskInfo", nullptr, GetTransientTaskInfo, nullptr, nullptr, nullptr, napi_default, nullptr },
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   EXTERN_C_END
   ```

3. Register the module.

   <!-- @[registration_module](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/NativeTransientTask/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
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

### Declaring the Functions in the index.d.ts File

   <!-- @[declaration_function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/NativeTransientTask/entry/src/main/cpp/types/libentry/Index.d.ts) -->

   ```ts
   import backgroundTaskManager from '@kit.BackgroundTasksKit';

   export const RequestSuspendDelay: () => number;
   export const GetRemainingDelayTime: () => number;
   export const CancelSuspendDelay: () => number;
   export const GetTransientTaskInfo: () => backgroundTaskManager.TransientTaskInfo;
   ```

### Calling the Functions in the index.ets File

   <!-- @[native_transient_task](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/BasicFeature/TaskManagement/NativeTransientTask/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import testTransientTask from 'libentry.so';

   @Entry
   @Component
   struct Index {
     @State message: string = '';

     build() {
       Row() {
         Column() {
           Text(this.message)
             .fontSize(50)
             .fontWeight(FontWeight.Bold)
           Button() {
             Text("RequestSuspendDelay").fontSize(20)
           }
           .margin({ top: 10, bottom: 10 })
           .width(250)
           .height(40)
           .backgroundColor('#0D9FFB')
           .onClick(() => {
             this.RequestSuspendDelay();
           })

           Button(){
             Text('GetRemainingDelayTime').fontSize(20)
           }
           .margin({ top: 10, bottom: 10 })
           .width(250)
           .height(40)
           .backgroundColor('#0D9FFB')
           .onClick(() => {
             this.GetRemainingDelayTime();
           })

           Button(){
             Text('CancelSuspendDelay').fontSize(20)
           }
           .margin({ top: 10, bottom: 10 })
           .width(250)
           .height(40)
           .backgroundColor('#0D9FFB')
           .onClick(() => {
             this.CancelSuspendDelay();
           })

           Button(){
             Text('GetTransientTaskInfo').fontSize(20)
           }
           .margin({ top: 10, bottom: 10 })
           .width(250)
           .height(40)
           .backgroundColor('#0D9FFB')
           .onClick(() => {
             this.GetTransientTaskInfo();
           })
         }
         .width('100%')
       }
       .height('100%')
     }

     RequestSuspendDelay() {
       let requestId = testTransientTask.RequestSuspendDelay();
       console.info('The return requestId is ' + requestId);
     }

     GetRemainingDelayTime() {
       let time = testTransientTask.GetRemainingDelayTime();
       console.info('The time is ' + time);
     }

     CancelSuspendDelay() {
       let ret = testTransientTask.CancelSuspendDelay();
       console.info('The ret is ' + ret);
     }

     GetTransientTaskInfo() {
       let ret = testTransientTask.GetTransientTaskInfo();
       console.info('The ret is ' + JSON.stringify(ret));
     }
   }
   ```

### Configuring the Library Dependency

Configure the `CMakeLists.txt` file. Add the required shared library, that is, `libtransient_task.so`, to `target_link_libraries` in the `CMakeLists.txt` file automatically generated by the project.

   ```txt
   target_link_libraries(entry PUBLIC libace_napi.z.so libtransient_task.so)
   ```

## How to Test

1. Connect to the device and run the program.

2. Tap the `Request transient task` button. The console prints a log. The following is an example:

   ```txt
   The return requestId is 1
   ```

3. Tap the `Obtain remaining time` button. The console prints a log. The following is an example:

   ```txt
   The return requestId is 18000
   ```
4. Tap the `Cancel transient task` button. The console prints a log. The following is an example:

   ```txt
   The ret is 0
   ```
5. Tap the `Obtain all transient task information` button. The console prints a log. The following is an example:

   ```txt
   The ret is {"remainingQuota":600000,"transientTasks":[]}
   ```
> **NOTE**
>
>If the `Request transient task` button is tapped for more than three consecutive times, the number of transient tasks exceeds the upper limit, and an error is reported. For more constraints, see [Transient Task (ArkTS)](transient-task.md#constraints).
