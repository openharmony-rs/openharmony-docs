# Using HiCollie to Detect Function Execution Timeout Events (C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @rr_cn-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

Task execution timeout indicates that the execution duration of the monitored service code logic exceeds the expected duration. This topic describes the capability of the HiCollie module to detect function execution timeout events.

## Available APIs

| API| Description|
| -------- | -------- |
| OH_HiCollie_SetTimer | Sets a timer to check whether the execution time of a function or code block exceeds the custom time.<br>This API is used before the time-consuming function is called. It must be used together with the **OH_HiCollie_CancelTimer** API.<br>Note: This API is supported since API version 18.|
| OH_HiCollie_CancelTimer | Cancels a timer based on task ID.<br>This API is used after the function or code block is executed. It must be used together with the **OH_HiCollie_SetTimer** API.<br>If the timer is not canceled within the custom time, a callback function is executed to generate fault logs for the specified timeout event.<br>Note: This API is supported since API version 18.|

- For details about how to use the APIs (such as parameter usage restrictions and value ranges), see [HiCollie](../reference/apis-performance-analysis-kit/capi-hicollie-h.md).

- The fault log file is saved in the **device/data/log/warninglog/** directory. The file name format is **syswarning-application bundle name-application UID-second-level time.log**.

## How to Develop

The following describes how to add a button in the application and click the button to call the HiCollie APIs.

1. Create a native C++ project. The directory structure is as follows:

   ```yml
   entry:
     src:
       main:
         cpp:
           types:
             libentry:
               - index.d.ts
           - CMakeLists.txt
           - napi_init.cpp
         ets:
           entryability:
             - EntryAbility.ts
           pages:
             - Index.ets
   ```

2. In the **CMakeLists.txt** file, add the source file and dynamic libraries.

   ```cmake
   # Add libhilog_ndk.z.so (log output) and libohhicollie.so (HiCollie external APIs).
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libohhicollie.so)
   ```

3. In the **napi_init.cpp** file, import dependency header files, define **LOG_TAG** and test methods, and register **TestHiCollieTimerNdk** as an ArkTS API.

   Import the header files and define **LOG_TAG**.

   <!-- @[EventSub_napi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   #include "napi/native_api.h"
   #include "json/json.h"
   #include "hilog/log.h"
   #include "hiappevent/hiappevent.h"
   #include "hiappevent/hiappevent_event.h"
   
   #undef LOG_TAG
   #define LOG_TAG "testTag"
   ```

   <!-- @[Hicollie_Set_Timer_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   #include <unistd.h>
   #include "hicollie/hicollie.h"
   ```

   Construct a scenario where the task execution times out, and use the **OH_HiCollie_SetTimer** and **OH_HiCollie_CancelTimer** functions to monitor the task.

   <!-- @[Hicollie_Set_Timer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Define the callback.
   void CallBack(void*)
   {
       OH_LOG_INFO(LogType::LOG_APP, "HiCollieTimerNdk CallBack");  // Logs are printed in the callback.
   }
   
   static napi_value TestHiCollieTimerNdk(napi_env env, napi_callback_info info)
   {
       int id;
       // Set HiCollieTimer parameters (timer task name, timeout interval, callback, callback parameters, and behavior after timeout).
       HiCollie_SetTimerParam param = {"testTimer", 1, CallBack, nullptr, HiCollie_Flag::HICOLLIE_FLAG_LOG};
       HiCollie_ErrorCode errorCode = OH_HiCollie_SetTimer(param, &id);  // Register a HiCollieTimer function to execute a one-off timeout detection task.
       if (errorCode == HICOLLIE_SUCCESS) {  // The HiCollieTimer task is successfully registered.
           OH_LOG_INFO(LogType::LOG_APP, "HiCollieTimer taskId: %{public}d", id); // Log the task ID.
           sleep (2); // Simulate a time-consuming function to block the thread for 2s.
           OH_HiCollie_CancelTimer (id); // Cancel the registered timer based on the ID.
       }
       return nullptr;
   }
   ```

   Register **TestHiCollieTimerNdk** as an ArkTS API in the **desc[]** array in the **Init** function.

   <!-- @[test_hicollie_timer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   // Register TestHiCollieTimerNdk as an ArkTS API.
   { "TestHiCollieTimerNdk", nullptr, TestHiCollieTimerNdk, nullptr, nullptr, nullptr, napi_default, nullptr },
   ```

4. In the **index.d.ts** file, define the ArkTS API.

   <!-- @[test_hicollie_timer_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->
   
   ``` TypeScript
   export const TestHiCollieTimerNdk: () => void;
   ```

5. Edit the **Index.ets** file.
   Import the header file for calling the C API.

   <!-- @[EventSub_Index_Capi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   import testNapi from 'libentry.so';
   ```

   Add a button on the **Index** page to trigger the **TestHiCollieTimerNdk** method.

   <!-- @[hicollie_timer_ndk_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Add a click event to trigger the TestHiCollieTimerNdk method.
   Button('TestHiCollieTimerNdk')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       testNapi.TestHiCollieTimerNdk();
     })
   ```

6. Click the **Run** button in DevEco Studio to run the project.

7. At the bottom of DevEco Studio, switch to the **Log** tab, choose **HiLog** and set the filter criteria to **testTag**.

   (1) Click the **testHiCollieTimerNdk** button to execute the timer, and the task ID is logged.

   ```
   .../testTag ... HiCollieTimer taskId: x
   ```

   (2) After 2s, the callback function is executed and logs are displayed.

   ```
   .../testTag ... HiCollieTimerNdk CallBack
   ```

   For details about how to obtain the fault file information, see [Subscribing to Task Execution Timeout Events (C/C++)](hiappevent-watcher-apphicollie-events-ndk.md).
