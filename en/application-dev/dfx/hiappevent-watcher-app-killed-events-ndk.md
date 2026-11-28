# Subscribing to Application Killed Events (C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7ee11c1f0301e6100e1f26dcd0b3d3ad99aef3fb translatedAt=2026-11-28T03:12:44.833Z nl=2 -->

## Event Specifications

For details, see [Application Killed Event Overview](./hiappevent-watcher-app-killed-events.md).

## Available APIs

For details about how to use the APIs (such as parameter usage restrictions and value ranges), see [HiAppEvent](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md).

**Subscription APIs**

| Name                                                      | Description                                        |
| ------------------------------------------------------------ | -------------------------------------------- |
| int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher *watcher)   | Adds a watcher to listen for application events.|
| int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher *watcher) | Removes a watcher for the specified application events.|

## How to Develop

1. Obtain the jsoncpp files required by the sample project. Open the [HiAppEvent EventSub sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub) and click **Download current directory** to download the EventSub project files.

2. In DevEco Studio, create a project using the Native C++ template and import the preceding files into the project. The directory structure is as follows:

   ```yml
   entry:
       libs:    // Directory for third-party libraries required by jsoncpp.
       src:
       main:
           cpp:
           thirdparty:
               jsoncpp:    // Directory for third-party libraries required by jsoncpp.
           types:
               libentry:
               - index.d.ts
           - CMakeLists.txt
           - napi_init.cpp
           ets:
           entryability:
               - EntryAbility.ets
           pages:
               - Index.ets
   ```

   The jsoncpp library files in this sample project use source code from the [third-party open-source jsoncpp library](https://codeload.github.com/open-source-parsers/jsoncpp/tar.gz/refs/tags/1.9.6).

3. Edit **entry > src > main > cpp > CMakeLists.txt** in the project and add source files and dynamic libraries.

   <!-- @[eventsub_cmake_code](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/CMakeLists.txt) -->
   
   ``` Text
   set(GZ_FILE "${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/jsoncpp/src/jsoncpp-1.9.6.tar.gz")
   set(DEST_DIR "${CMAKE_CURRENT_SOURCE_DIR}/../../../build")
   # Check whether the entry/build directory exists.
   execute_process(COMMAND ${CMAKE_COMMAND} -E make_directory ${DEST_DIR})
   # Extract jsoncpp-1.9.6.tar.gz into entry/build to obtain the directory containing the jsoncpp header files.
   execute_process(COMMAND tar -xzf ${GZ_FILE} -C ${DEST_DIR}
       WORKING_DIRECTORY ${DEST_DIR})
   
   add_library(entry SHARED napi_init.cpp)
   # Add **libhiappevent_ndk.z.so** and **libhilog_ndk.z.so** (log output).
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libhiappevent_ndk.z.so)
   # Add the third-party library dependency libjsoncpp.so to parse JSON strings in subscribed events.
   target_link_libraries(entry PRIVATE ${CMAKE_CURRENT_SOURCE_DIR}/thirdparty/jsoncpp/${OHOS_ARCH}/lib/libjsoncpp.so)
   target_include_directories(entry PRIVATE ${DEST_DIR}/jsoncpp-1.9.6/include/json)
   ```

4. Edit **entry > src > main > cpp > napi_init.cpp** in the project, include the required files, and define **LOG_TAG**.

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

   onReceive observer:

   Edit **entry > src > main > cpp > napi_init.cpp** in the project, define the methods for an **onReceive** observer, and add a native memory leak method:

   <!-- @[AppKillEvent_OnReceive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) --> 
   
   ``` C++
   // Define a variable to cache the pointer to the created watcher.
   static HiAppEvent_Watcher *appKillWatcherR;
   
   static void HandleAppKillEventInfo(const struct HiAppEvent_AppEventInfo &appEventInfos)
   {
       OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.domain=%{public}s", appEventInfos.domain);
       OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.name=%{public}s", appEventInfos.name);
       OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.eventType=%{public}d", appEventInfos.type);
       if (strcmp(appEventInfos.domain, DOMAIN_OS) == 0 &&
           strcmp(appEventInfos.name, EVENT_APP_KILLED) == 0) {
           Json::Value params;
           Json::Reader reader(Json::Features::strictMode());
           Json::FastWriter writer;
           if (reader.parse(appEventInfos.params, params)) {
               auto time = params["time"].asInt64();
               auto reason = params["reason"].asString();
               auto foreground = params["foreground"].asString();
               auto callingPid = params["calling_pid"].asString();
               auto callingProcessName = params["calling_process_name"].asString();
               auto appRunningUniqueId = params["app_running_unique_id"].asString();
               auto bundleVersion = params["bundle_version"].asString();
               auto lastExitDetailInfo = writer.write(params["last_exit_detail_info"]);
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.time=%{public}lld", time);
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.reason=%{public}s", reason.c_str());
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.foreground=%{public}s", foreground.c_str());
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.calling_pid=%{public}s", callingPid.c_str());
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.calling_process_name=%{public}s",
                   callingProcessName.c_str());
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.app_running_unique_id=%{public}s",
                   appRunningUniqueId.c_str());
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version=%{public}s",
                   bundleVersion.c_str());
               OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.last_exit_detail_info=%{public}s",
                   lastExitDetailInfo.c_str());
           }
       }
   }
   
   static void OnReceiveAppKillEvent(const char *domain, const struct HiAppEvent_AppEventGroup *appEventGroups,
       uint32_t groupLen)
   {
       for (int i = 0; i < groupLen; ++i) {
           for (int j = 0; j < appEventGroups[i].infoLen; ++j) {
               HandleAppKillEventInfo(appEventGroups[i].appEventInfos[j]);
           }
       }
   }
   
   static napi_value RegisterAppKillWatcher(napi_env env, napi_callback_info info)
   {
       OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent RegisterWatcher");
       // Set the watcher name. The system identifies different watchers based on their names.
       appKillWatcherR = OH_HiAppEvent_CreateWatcher("onAppKillReceiverWatcher");
       // Set the event to watch to EVENT_APP_KILLED.
       const char *names[] = {EVENT_APP_KILLED};
       // Add the events to watch, for example, system events.
       OH_HiAppEvent_SetAppEventFilter(appKillWatcherR, DOMAIN_OS, 0, names, 1);
       // Set the implemented callback function. When the watcher receives an event, the OnReceive callback is triggered immediately.
       OH_HiAppEvent_SetWatcherOnReceive(appKillWatcherR, OnReceiveAppKillEvent);
       // Add a watcher to listen for the specified event.
       int ret = OH_HiAppEvent_AddWatcher(appKillWatcherR);
       if (ret != 0) {
           OH_LOG_ERROR(LogType::LOG_APP, "HiAppEvent AddWatcher failed, ret=%{public}d", ret);
       }
       return {};
   }
   ```

6. Implement **Leak** for fault injection and self-testing only; do not integrate it into your application logic. Edit **entry > src > main > cpp > napi_init.cpp** in the project and add the header files:

   <!-- @[AppKillEvent_NativeLeak_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   #include <thread>
   ```

   Edit **entry > src > main > cpp > napi_init.cpp** in the project and add the **NativeLeak** and **Leak** methods:

   <!-- @[AppKillEvent_NativeLeak](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   
   static void NativeLeak()
   {
       constexpr int leakSizePerTime = 500000;
       constexpr int sleepTimeMs = 10;
       while (true) {
           char *p = (char *)malloc(leakSizePerTime + 1);
           if (!p) {
               break;
           }
           memset(p, 'a', leakSizePerTime);
           std::this_thread::sleep_for(std::chrono::milliseconds(sleepTimeMs));
       }
   }
   
   static napi_value Leak(napi_env env, napi_callback_info info)
   {
       std::thread t1(NativeLeak);
       t1.detach();
       return {};
   }
   ```

7. Edit **entry > src > main > cpp > napi_init.cpp** in the project and register **RegisterAppKillWatcher** and **Leak** as ArkTS APIs:

   <!-- @[AppKillEvent_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           // ...
           { "registerAppKillWatcher", nullptr, RegisterAppKillWatcher, nullptr, nullptr, nullptr,
               napi_default, nullptr },
           { "leak", nullptr, Leak, nullptr, nullptr, nullptr, napi_default, nullptr},
           // ...
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   ```

   Edit **entry > src > main > cpp > types > libentry > Index.d.ts** in the project and define the ArkTS APIs:

   <!-- @[AppKillEvent_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->
   
   ``` TypeScript
   export const registerAppKillWatcher: () => void;
   export const leak: () => void;
   ```

8. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, add the following API invocation to **onCreate()**:

   <!-- @[AppKillEvent_Call_Capi_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // Add the API to onCreate().
   // Register the system event watcher at startup.
   testNapi.registerAppKillWatcher();
   
   // Trigger a leak when the button is operated or started.
   testNapi.leak();
   ```

9. Click the **Run** button in DevEco Studio to run the project. After the leak is triggered, wait for 2 to 3 minutes and the application exits.

10. After the application is killed, open the application again. The killed event is reported, and the system calls **onReceive()**. You can view the following event information in the **Log** window:

    ``` Text
      HiAppEvent eventInfo.domain=OS
      HiAppEvent eventInfo.name=APP_KILLED
      HiAppEvent eventInfo.eventType=2
      HiAppEvent eventInfo.params.time=1792739581978
      HiAppEvent eventInfo.params.reason="RssThresholdKiller"
      HiAppEvent eventInfo.params.foreground=true
      HiAppEvent eventInfo.params.calling_pid="43"
      HiAppEvent eventInfo.params.calling_process_name="wk:0/0/1/12"
      HiAppEvent eventInfo.params.app_running_unique_id=8778602711597370439
      HiAppEvent eventInfo.params.bundle_version=1.0.1
      HiAppEvent eventInfo.params.last_exit_detail_info={"exit_msg":"","kill_reason":"RssThresholdKiller","pid":"17248","process_name":"com.example.dfx_test","process_state":"2","pss":"227764","rss":"227764","timestamp":"1792739581947","uid":"20020207"}
    ```

    > **NOTE**
    >
    > For details about the error information, see [Application Killed Event Overview](./hiappevent-watcher-app-killed-events.md#field-description).

11. Remove the event watcher:

    <!-- @[AppKillEvent_Remove_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value RemoveAppKillWatcher(napi_env env, napi_callback_info info)
    {
        // Remove the watcher.
        OH_HiAppEvent_RemoveWatcher(appKillWatcherR);
        return {};
    }
    ```

12. Destroy the event watcher:

    <!-- @[AppKillEvent_Destroy_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
    
    ``` C++
    static napi_value DestroyAppKillWatcher(napi_env env, napi_callback_info info)
    {
        // Destroy the created watcher and set appKillWatcherR to nullptr.
        OH_HiAppEvent_DestroyWatcher(appKillWatcherR);
        appKillWatcherR = nullptr;
        return {};
    }
    ```
