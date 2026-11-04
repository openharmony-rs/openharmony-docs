# Subscribing to Main Thread Jank Events (C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8d3fbd9cea938deab591400a098c0e0ae9d431c9 translatedAt=2026-11-04T06:35:05.446Z pushedAt=2026-11-04T06:35:05.446Z nl=1 -->

## Overview

This section describes how to use the C/C++ APIs provided by HiAppEvent to subscribe to main thread timeout events. For detailed API usage instructions (parameter constraints, value ranges, etc.), refer to [hiappevent.h](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md).

## Available APIs

| API| Description|
| -------- | -------- |
| int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher \*watcher) | Adds a watcher to listen for application events.|
| int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher \*watcher) | Removes a watcher to unsubscribe from application events.|

## How to Develop

### Adding an Event Watcher

The following example shows how to trigger a main thread jank event when a user clicks a button:

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

4. Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to import the required files and define `LOG_TAG`.

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

5. Subscribe to system events.

    Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to define the methods related to the watcher of the **onReceive** type:

    <!-- @[MainThreadJank_OnReceive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    // Define a variable to cache the pointer of the created watcher.
    static HiAppEvent_Watcher *systeMainThreadJankEventWatcher;

    static void HandleMainThreadJankEventInfo(const struct HiAppEvent_AppEventInfo &appEventInfos)
    {
        OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.domain=%{public}s", appEventInfos.domain);
        OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.name=%{public}s", appEventInfos.name);
        OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.eventType=%{public}d", appEventInfos.type);
        if (strcmp(appEventInfos.domain, DOMAIN_OS) == 0 &&
            strcmp(appEventInfos.name, EVENT_MAIN_THREAD_JANK) == 0) {
            Json::Value params;
            Json::Reader reader(Json::Features::strictMode());
            Json::FastWriter writer;
            if (reader.parse(appEventInfos.params, params)) {
                auto time = params["time"].asInt64();
                auto pid = params["pid"].asInt();
                auto uid = params["uid"].asInt();
                auto bundleName = params["bundle_name"].asString();
                auto bundleVersion = params["bundle_version"].asString();
                auto beginTime = params["begin_time"].asInt64();
                auto endTime = params["end_time"].asInt64();
                auto externalLog = writer.write(params["external_log"]);
                auto logOverLimit = params["logOverLimit"].asBool();
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.time=%{public}lld", time);
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.pid=%{public}d", pid);
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uid=%{public}d", uid);
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_name=%{public}s",
                            bundleName.c_str());
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version=%{public}s",
                            bundleVersion.c_str());
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.begin_time=%{public}lld", beginTime);
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.end_time=%{public}lld", endTime);
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.external_log=%{public}s",
                            externalLog.c_str());
                OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.log_over_limit=%{public}d",
                            logOverLimit);
            }
        }
    }

    static void OnMainThreadJankReceive(const char *domain, const struct HiAppEvent_AppEventGroup *appEventGroups,
        uint32_t groupLen)
    {
        for (int i = 0; i < groupLen; ++i) {
            for (int j = 0; j < appEventGroups[i].infoLen; ++j) {
                HandleMainThreadJankEventInfo(appEventGroups[i].appEventInfos[j]);
            }
        }
    }

    static napi_value RegisterMainThreadJankWatcher(napi_env env, napi_callback_info info)
    {
        OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent MainThreadJank RegisterMainThreadJankWatcher");
        // Set the watcher name. The system identifies different watchers based on their names.
        systeMainThreadJankEventWatcher = OH_HiAppEvent_CreateWatcher("MainThreadJankReceiverWatcher");
        // Set the event to subscribe to EVENT_MAIN_THREAD_JANK.
        const char *names[] = {EVENT_MAIN_THREAD_JANK};
        // Add the events to watch, for example, system events.
        OH_HiAppEvent_SetAppEventFilter(systeMainThreadJankEventWatcher, DOMAIN_OS, 0, names, 1);
        // Set the implemented callback. OnMainThreadJankReceive is triggered as soon as the watcher receives an event.
        OH_HiAppEvent_SetWatcherOnReceive(systeMainThreadJankEventWatcher, OnMainThreadJankReceive);
        // Add a watcher to listen for the specified event.
        OH_HiAppEvent_AddWatcher(systeMainThreadJankEventWatcher);
        return {};
    }
    ```

6. Register **RegisterMainThreadJankWatcher** as an ArkTS API.

   Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to register `RegisterMainThreadJankWatcher` as an ArkTS API:

   <!-- @[MainThreadJank_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

   ``` C++
   { "RegisterMainThreadJankWatcher", nullptr, RegisterMainThreadJankWatcher, nullptr, nullptr, nullptr,
       napi_default, nullptr },
   ```

   Edit the **Index.d.ts** file under **entry > src > main > cpp > types > libentry** in the project to define the ArkTS API:

   <!-- @[MainThreadJank_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->

   ``` TypeScript
   export const RegisterMainThreadJankWatcher: () => void;
   ```

7. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, add the following API call to **onCreate()**.

    Import the dependency module.
   <!-- @[MainThreadJank_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->

   ``` TypeScript
   import testNapi from 'libentry.so';
   ```

   <!-- @[MainThreadJank_Event_Call_Capi_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // Add the API call in the onCreate() function.
   // Register the system event watcher at startup.
   testNapi.RegisterMainThreadJankWatcher();
   ```

8. Edit the **Index.ets** file under **entry > src > main > ets > pages** in the project to add a button. In its **onClick** callback, simulate a main thread timeout to trigger a main thread jank event. The sample code is as follows:

   <!-- @[MainThreadJank_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->

   ``` TypeScript
   // Add a click handler to trigger MAIN_THREAD_JANK.
   Button('timeOut350')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       let t = Date.now();
       while (Date.now() - t <= 350) {}
     })
   ```

9. In DevEco Studio, click the **Run** button to run the application project. Click the **timeOut350** button twice or three times consecutively to trigger a main thread jank event.

### Verifying the Subscription

1. After the main thread jank event is reported, you can view the following event information in the **Log** window.

   ```text
     HiAppEvent eventInfo.domain=OS
     HiAppEvent eventInfo.name=MAIN_THREAD_JANK
     HiAppEvent eventInfo.eventType=1
     HiAppEvent eventInfo.params.time=1717597063727
     HiAppEvent eventInfo.params.pid=45572
     HiAppEvent eventInfo.params.uid=20020151
     HiAppEvent eventInfo.params.bundle_name=com.example.nativemainthread
     HiAppEvent eventInfo.params.bundle_version=1.0.0
     HiAppEvent eventInfo.params.begin_time=1717597063225
     HiAppEvent eventInfo.params.end_time=1717597063727
     HiAppEvent eventInfo.params.external_log=["/data/storage/el2/log/watchdog/MAIN_THREAD_JANK_20240613221239_45572.txt"]
     HiAppEvent eventInfo.params.log_over_limit=0
   ```

    > **NOTE**
    >
    > For details about the main thread jank event specifications, see [main thread jank event detection principles](apptask-timeout-guidelines.md#detection-principles) and [main thread jank event log specifications](apptask-timeout-guidelines.md#log-specifications).

### Removing and Destroying an Event Watcher

1. Remove the event watcher.

    <!-- @[MainThreadJankEvent_RemoveWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value RemoveWatcher(napi_env env, napi_callback_info info)
    {
        // Stop listening for events.
        // ...
        OH_HiAppEvent_RemoveWatcher(systeMainThreadJankEventWatcher);
        return {};
    }
    ```

2. Destroy the event watcher.

    <!-- @[MainThreadJankEvent_DestroyWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->

    ``` C++
    static napi_value DestroyWatcher(napi_env env, napi_callback_info info)
    {
        // Destroy the watcher and set the watcher pointer to nullptr.
        // ...
        OH_HiAppEvent_DestroyWatcher(systeMainThreadJankEventWatcher);
        systeMainThreadJankEventWatcher = nullptr;
        return {};
    }
    ```