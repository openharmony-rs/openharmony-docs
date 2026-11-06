# Subscribing to Task Execution Timeout Events (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=55475b8d201845bcd9989a5f64cef91cd4c2751f translatedAt=2026-11-03T13:00:53.698Z pushedAt=2026-11-03T13:00:53.698Z nl=1 -->

## Overview

Starting from API version 21, you can use ArkTS APIs to subscribe to task execution timeout events. This document describes how to use the ArkTS APIs provided by HiAppEvent to subscribe to task execution timeout events. For detailed API usage instructions (such as parameter constraints and value ranges), see [@ohos.hiviewdfx.hiAppEvent](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

## Available APIs

| Name| Description|
| -------- | -------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | Adds a watcher to listen for application events.|
| removeWatcher(watcher: Watcher): void | Removes a watcher to unsubscribe from application events.|

## How to Develop

### Adding an Event Watcher

To ensure that event callbacks can be successfully received in the development phase, you are advised to create a native C++ project, implement subscription in the ArkTS code, and use C++ code to construct fault injection to trigger task execution timeout events.

1. Obtain the jsoncpp files required by the sample project. Open [HiAppEvent EventSub Sample](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub) and click **Download current directory** to download the EventSub project files.

2. In DevEco Studio, create a project using the Native C++ template and import the downloaded files into the project. The directory structure is as follows.

   ```yml
   entry:
     libs:    //  Directory for third-party libraries required by jsoncpp.
     src:
       main:
         cpp:
           - thirdparty:
               jsoncpp:    //  Directory for third-party libraries required by jsoncpp.
           - types:
               libentry:
                 - index.d.ts
           - CMakeLists.txt
           - napi_init.cpp
         ets:
           - entryability:
               - EntryAbility.ets
           - pages:
               - Index.ets
   ```

   The source code for the jsoncpp library in this sample project comes from [JsonCpp](https://codeload.github.com/open-source-parsers/jsoncpp/tar.gz/refs/tags/1.9.6).

3. Edit the **entry > src > main > cpp > CMakeLists.txt** file in the project to add source files and dynamic libraries.

   ```cmake
   add_library(entry SHARED napi_init.cpp)
   # Add dependencies on libhiappevent_ndk.z.so and libhilog_ndk.z.so (for log output).
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libhiappevent_ndk.z.so)
   set(GZ_FILE "${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/jsoncpp/src/jsoncpp-1.9.6.tar.gz")
   set(DEST_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../../../build")
   # Ensure that the entry/build directory exists.
   execute_process(COMMAND ${CMAKE_COMMAND} -E make_directory ${DEST_DIR})
   # Extract jsoncpp-1.9.6.tar.gz to entry/build to obtain the jsoncpp header directory.
   execute_process(COMMAND tar -xzf ${GZ_FILE} -C ${DEST_DIR}
       WORKING_DIRECTORY ${DEST_DIR})

   # Add the third-party library libjsoncpp.so to parse JSON strings in subscribed events.
   target_link_libraries(entry PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/jsoncpp/${OHOS_ARCH}/lib/libjsoncpp.so)
   target_include_directories(entry PRIVATE ${DEST_DIR}/jsoncpp-1.9.6/include/json)
   ```

4. Edit the **entry > src > main > ets > entryability > EntryAbility.ets** file in the project to import the dependency modules. The sample code is as follows:

   <!-- @[AppHicollie_ArkTS_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
   ```

5. Subscribe to system events. Edit the **entry > src > main > ets > entryability > EntryAbility.ets** file in the project and add the subscription code to **onCreate**. The sample code is as follows:

   <!-- @[appHicollieWatcher_Watcher_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   let appHicollieWatcher: hiAppEvent.Watcher;
   ```

   <!-- @[AppHicollie_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   // Subscribe to task execution timeout events.
   appHicollieWatcher = {
     // You can customize the watcher name. The system uses the name to identify different watchers.
     name: "appHicollieWatcher",
     // Subscribe to the system events of interest. Here, task execution timeout events are subscribed to.
     appEventFilters: [
       {
         domain: hiAppEvent.domain.OS,
         names: [hiAppEvent.event.APP_HICOLLIE]
       }
     ],
     // Implement the real-time subscription callback to customize the processing of subscribed event data.
     onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
       hilog.info(0x0000, 'testTag', `HiAppEvent onReceive: domain=${domain}`);
       for (const eventGroup of appEventGroups) {
         hilog.info(0x0000, 'testTag', `HiAppEvent eventName=${eventGroup.name}`);
         for (const eventInfo of eventGroup.appEventInfos) {
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.domain=${eventInfo.domain}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.name=${eventInfo.name}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.eventType=${eventInfo.eventType}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.time=${eventInfo.params['time']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.foreground=${eventInfo.params['foreground']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version=${eventInfo.params['bundle_version']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.process_name=${eventInfo.params['process_name']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.pid=${eventInfo.params['pid']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.uid=${eventInfo.params['uid']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.uuid=${eventInfo.params['uuid']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.exception=${eventInfo.params['exception']}`);
           if (eventInfo.params['hilog'] != undefined) {
             hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.hilog.size=${eventInfo.params['hilog'].length}`);
           }
           if (eventInfo.params['peer_binder'] != undefined) {
             hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.peer_binder.size=${JSON.stringify(eventInfo.params['peer_binder'].length)}`);
           }
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.memory=${eventInfo.params['memory']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.external_log=${JSON.stringify(eventInfo.params['external_log'])}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.log_over_limit=${eventInfo.params['log_over_limit']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.external_callback_log=${eventInfo.params['external_callback_log']}`);
         }
       }
     }
   };
   hiAppEvent.addWatcher(appHicollieWatcher);
   ```

6. Add the **HiCollieTestTimerNdk** function.

   Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to include the required header files and define `LOG_TAG`.

    <!-- @[EventSub_napi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    #include "napi/native_api.h"
    // Adjust the path to json.h based on the location of the third-party jsoncpp library in the project.
    #include "../../../build/jsoncpp-1.9.6/include/json/json.h"
    #include "hiappevent/hiappevent.h"
    #include "hiappevent/hiappevent_param.h"
    #include "hilog/log.h"

    #undef LOG_TAG
    #define LOG_TAG "testTag"
    ```

   Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to add the `HiCollieTestTimerNdk` function, which triggers a task execution timeout event:

   <!-- @[Hicollie_Set_Timer_h](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   #include <unistd.h>
   #include "hicollie/hicollie.h"
   ```

   Simulate a task execution timeout and use `OH_HiCollie_SetTimer` and `OH_HiCollie_CancelTimer` to monitor it.

   <!-- @[Hicollie_Test_Set_Timer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   static napi_value HiCollieTestTimerNdk(napi_env env, napi_callback_info exports)
   {
       // Define the task execution timeout ID.
       int id;
       // Define the task timeout detection parameters: a timeout threshold of 1 second and log generation as the action.
       HiCollie_SetTimerParam param = {"testTimer", 1, nullptr, nullptr, HiCollie_Flag::HICOLLIE_FLAG_LOG};
       // Set up timeout detection.
       HiCollie_ErrorCode errorCode = OH_HiCollie_SetTimer(param, &id);
       if (errorCode == HICOLLIE_SUCCESS) {
           OH_LOG_INFO(LogType::LOG_APP, "Timer Id is %{public}d", id);
           // Simulate a 2-second timeout.
           sleep(2);
           OH_HiCollie_CancelTimer(id);
       } else {
           OH_LOG_INFO(LogType::LOG_APP, "OH_HiCollie_SetTimer failed, errorCode is %{public}d", errorCode);
       }
       return nullptr;
   }
   ```

7. Register **HiCollieTestTimerNdk** as an ArkTS API.

   Edit the **entry > src > main > cpp > napi_init.cpp** file in the project and register `HiCollieTestTimerNdk` as an ArkTS API in the `desc[]` array of the `Init` function:

   <!-- @[test_hicollie_set_timer](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   // Register HiCollieTestTimerNdk as an ArkTS API.
   { "HiCollieTestTimerNdk", nullptr, HiCollieTestTimerNdk, nullptr, nullptr, nullptr, napi_default, nullptr },
   ```

   Edit the **Index.ets** file under **entry > src > main > cpp > types > libentry** in the project to define the ArkTS API.

   <!-- @[test_hicollie_set_timer_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->

   ``` TypeScript
   export const HiCollieTestTimerNdk: () => void;
   ```

8. Edit the **Index.ets** file under **entry > src > main > ets > pages** in the project to add a button that triggers the task execution timeout event.

   Import the module for calling the C API.

   <!-- @[EventSub_Index_Capi_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   import testNapi from 'libentry.so';
   ```

   Add a button to the Index page to call `HiCollieTestTimerNdk`.

   <!-- @[hicollie_set_timer_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // Add a click handler to call HiCollieTestTimerNdk.
   Button('HiCollieTestTimerNdk')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       testNapi.HiCollieTestTimerNdk();
     })
   ```

9. In DevEco Studio, click the **Run** button to run the project. Then, click the **HiCollieTestTimerNdk** button to trigger a task execution timeout event.

### Verifying the Subscription

After the project crashes and exits, restart it. You can view the system event data processing logs in the **Log** window.

   ```text
   HiAppEvent eventInfo.domain=OS
   HiAppEvent eventInfo.name=APP_HICOLLIE
   HiAppEvent eventInfo.eventType=1
   HiAppEvent eventInfo.params.time=1754914806680
   HiAppEvent eventInfo.params.foreground=true
   HiAppEvent eventInfo.params.bundle_version=1.0.0
   HiAppEvent eventInfo.params.process_name=com.example.myapplication
   HiAppEvent eventInfo.params.pid=20317
   HiAppEvent eventInfo.params.uid=20020198
   HiAppEvent eventInfo.params.uuid=4asd360e18f5d6d84cf4f0c9e80d66we5786c1cc2343d9632e07abb0d3552asd
   HiAppEvent eventInfo.params.exception={"message":"","name":"APP_HICOLLIE"}
   HiAppEvent eventInfo.params.hilog.size=28
   HiAppEvent eventInfo.params.peer_binder.size=0
   HiAppEvent eventInfo.params.memory={"pss":0,"rss":150748,"sys_avail_mem":5387264,"sys_free_mem":218902,"sys_total_mem":11679236,"vss":38306936}
   HiAppEvent eventInfo.params.external_log=["/data/storage/el2/log/hiappevent/APP_HICOLLIE_1754914811140_20317.log"]
   HiAppEvent eventInfo.params.log_over_limit=false
   HiAppEvent eventInfo.params.external_callback_log=THREAD_BLOCK_3S:log3s THREAD_BLOCK_6S:log6s
   ```

### Removing an Event Watcher

Remove the event watcher in **onDestroy**. The sample code is as follows:

<!-- @[remove_hicollie_watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

``` TypeScript
// Remove the application event watcher to unsubscribe from events.
hiAppEvent.removeWatcher(appHicollieWatcher);
```
