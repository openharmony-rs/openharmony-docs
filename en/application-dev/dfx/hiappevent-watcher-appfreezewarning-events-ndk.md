# Subscribing to App Freeze Warning Events (C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7ee11c1f0301e6100e1f26dcd0b3d3ad99aef3fb translatedAt=2026-11-28T03:12:44.836Z nl=2 -->

## Overview

This section describes how to use the C/C++ APIs provided by HiAppEvent to subscribe to app freeze warning events. For detailed API usage instructions (parameter constraints, value ranges, etc.), refer to [hiappevent.h](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md).

## Available APIs

| Name | Description |
| -------- | -------- |
| int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher \*watcher) | Adds an app event watcher to subscribe to app events. |
| int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher \*watcher) | Removes an app event watcher to unsubscribe from app events. |

## How to Develop

### Adding an Event Watcher

The following uses subscribing to app freeze warning events as an example to illustrate the development procedure.

1. Obtain the jsoncpp files required by the sample project. Open the [HiAppEvent EventSub sample project](https://gitcode.com/openharmony/applications_app_samples/tree/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub) and click **Download current directory** to download the EventSub project files.

2. In DevEco Studio, create a project using the Native C++ template and import the preceding files into the project. The directory structure is as follows:

   ```yml
   entry:
     libs:    // Directory for third-party libraries required by jsoncpp.
     src:
       main:
         cpp:
           - thirdparty:
               jsoncpp:    // Directory for third-party libraries required by jsoncpp.
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
   # Add the dynamic library dependencies libhiappevent_ndk.z.so and libhilog_ndk.z.so (for log output).
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

   - **onReceive** watcher:

      Edit **entry > src > main > cpp > napi_init.cpp** in the project and define the methods for an **onReceive** observer:

      <!-- @[AppFreezeWarning_OnReceive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
      
      ``` C++
      // Define a variable to cache the pointer of the created watcher.
      static HiAppEvent_Watcher *appFreezeWarningWatcherR;
      
      // Extract log output into a separate function because OnReceiveAppFreezeWarning exceeds the 50-line limit.
      static void AppFreezeWarningEventOutput(Json::Value params, Json::FastWriter writer)
      {
          auto time = params["time"].asInt64();
          auto foreground = params["foreground"].asBool();
          auto appRunningUniqueId = params["app_running_unique_id"].asString();
          auto bundleVersion = params["bundle_version"].asString();
          auto bundle_version_code = params["bundle_version_code"].asInt();
          auto bundleName = params["bundle_name"].asString();
          auto processName = params["process_name"].asString();
          auto pid = params["pid"].asInt();
          auto uid = params["uid"].asInt();
          auto exception = writer.write(params["exception"]);
          auto hilogSize = params["hilog"].size();
          auto handleSize = params["event_handler"].size();
          auto peerBindSize = params["peer_binder"].size();
          auto threadSize = params["threads"].size();
          auto memory = writer.write(params["memory"]);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.time=%{public}lld", time);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.foreground=%{public}d", foreground);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.app_running_unique_id=%{public}s",
              appRunningUniqueId.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version=%{public}s",
              bundleVersion.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version_code=%{public}d",
              bundle_version_code);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_name=%{public}s",
              bundleName.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.process_name=%{public}s",
              processName.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.pid=%{public}d", pid);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uid=%{public}d", uid);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.exception=%{public}s",
              exception.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.hilog.size=%{public}d", hilogSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler.size=%{public}d",
              handleSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.peer_binder.size=%{public}d",
              peerBindSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.threads.size=%{public}d",
              threadSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.memory=%{public}s",
              memory.c_str());
      }
      
      static void HandleAppFreezeWarningEvent(const struct HiAppEvent_AppEventInfo &appEventInfos)
      {
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.domain=%{public}s", appEventInfos.domain);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.name=%{public}s", appEventInfos.name);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.eventType=%{public}d", appEventInfos.type);
          if (strcmp(appEventInfos.domain, DOMAIN_OS) == 0 &&
              strcmp(appEventInfos.name, OH_EVENT_APP_FREEZE_WARNING) == 0) {
              Json::Value params;
              Json::Reader reader(Json::Features::strictMode());
              Json::FastWriter writer;
              if (reader.parse(appEventInfos.params, params)) {
                  AppFreezeWarningEventOutput(params, writer);
              }
          }
      }
      
      static void OnReceiveAppFreezeWarning(const char *domain, const struct HiAppEvent_AppEventGroup *appEventGroups,
          uint32_t groupLen)
      {
          for (int i = 0; i < groupLen; ++i) {
              for (int j = 0; j < appEventGroups[i].infoLen; ++j) {
                  HandleAppFreezeWarningEvent(appEventGroups[i].appEventInfos[j]);
              }
          }
      }
      
      static napi_value RegisterAppFreezeWarningReceiveWatcher(napi_env env, napi_callback_info info)
      {
          // Define a custom watcher name. The system identifies different watchers by their names.
          appFreezeWarningWatcherR = OH_HiAppEvent_CreateWatcher("onAppFreezeWarningReceiverWatcher");
          // Set the subscribed event to OH_EVENT_APP_FREEZE_WARNING.
          const char *names[] = {OH_EVENT_APP_FREEZE_WARNING};
          // Subscribe to events of interest. Here, a system event is subscribed to.
          OH_HiAppEvent_SetAppEventFilter(appFreezeWarningWatcherR, DOMAIN_OS, 0, names, 1);
          // Set the implemented callback function. The OnReceive callback is triggered immediately after the watcher receives an event.
          OH_HiAppEvent_SetWatcherOnReceive(appFreezeWarningWatcherR, OnReceiveAppFreezeWarning);
          // Start listening for subscribed events with the watcher.
          OH_HiAppEvent_AddWatcher(appFreezeWarningWatcherR);
          return {};
      }
      ```

   - **onTrigger** watcher:

      Edit **entry > src > main > cpp > napi_init.cpp** in the project and define the methods for an **OnTrigger** observer:

      <!-- @[AppFreezeWarning_OnTrigger](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
      
      ``` C++
      // Define a variable to cache the pointer of the created watcher.
      static HiAppEvent_Watcher *appFreezeWarningWatcherT;
      
      // Extract log output into a separate function because OnTakeAppFreezeWarning exceeds the 50-line limit.
      static void OnAppFreezeWarningEventOutPut(std::string domain, std::string name, Json::Value eventInfo,
          Json::FastWriter writer)
      {
          if (domain == DOMAIN_OS && name == OH_EVENT_APP_FREEZE_WARNING) {
              auto time = eventInfo["time"].asInt64();
              auto foreground = eventInfo["foreground"].asBool();
              auto appRunningUniqueId = eventInfo["app_running_unique_id"].asString();
              auto bundleVersion = eventInfo["bundle_version"].asString();
              auto bundle_version_code = eventInfo["bundle_version_code"].asInt();
              auto bundleName = eventInfo["bundle_name"].asString();
              auto processName = eventInfo["process_name"].asString();
              auto pid = eventInfo["pid"].asInt();
              auto uid = eventInfo["uid"].asInt();
              auto exception = writer.write(eventInfo["exception"]);
              auto hilogSize = eventInfo["hilog"].size();
              auto handleSize = eventInfo["event_handler"].size();
              auto peerBindSize = eventInfo["peer_binder"].size();
              auto threadSize = eventInfo["threads"].size();
              auto memory = writer.write(eventInfo["memory"]);
              auto process_life_time = eventInfo["process_life_time"].asString();
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.time=%{public}lld", time);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.foreground=%{public}d", foreground);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.app_running_unique_id=%{public}s",
                  appRunningUniqueId.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version=%{public}s",
                  bundleVersion.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version_code=%{public}d",
                  bundle_version_code);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_name=%{public}s",
                  bundleName.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.process_name=%{public}s",
                  processName.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.pid=%{public}d", pid);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uid=%{public}d", uid);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.exception=%{public}s",
                  exception.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.hilog.size=%{public}d", hilogSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler.size=%{public}d",
                  handleSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.peer_binder.size=%{public}d",
                  peerBindSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.threads.size=%{public}d",
                  threadSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.memory=%{public}s",
                  memory.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.process_life_time=%{public}s",
                  process_life_time.c_str());
          }
      }
      
      // Implement a callback to obtain monitored events. The content pointed to by the events pointer is valid only within this function.
      static void OnTakeAppFreezeWarning(const char *const *events, uint32_t eventLen)
      {
          Json::Reader reader(Json::Features::strictMode());
          Json::FastWriter writer;
          for (int i = 0; i < eventLen; ++i) {
              Json::Value eventInfo;
              if (reader.parse(events[i], eventInfo)) {
                  auto domain = eventInfo["domain_"].asString();
                  auto name = eventInfo["name_"].asString();
                  auto type = eventInfo["type_"].asInt();
                  OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.domain=%{public}s", domain.c_str());
                  OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.name=%{public}s", name.c_str());
                  OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.eventType=%{public}d", type);
                  // Process the application freeze warning event.
                  OnAppFreezeWarningEventOutPut(domain, name, eventInfo, writer);
              }
          }
      }
      
      // Implement a subscription callback to perform custom processing on the obtained event data.
      static void OnTriggerAppFreezeWarning(int row, int size)
      {
          // After receiving the callback, obtain the specified number of received events.
          OH_HiAppEvent_TakeWatcherData(appFreezeWarningWatcherT, row, OnTakeAppFreezeWarning);
      }
      
      static napi_value RegisterAppFreezeWarningTriggerWatcher(napi_env env, napi_callback_info info)
      {
          // Define a custom watcher name. The system identifies different watchers by their names.
          appFreezeWarningWatcherT = OH_HiAppEvent_CreateWatcher("onAppFreezeWarningTriggerWatcher");
          // Set the subscribed event to OH_EVENT_APP_FREEZE_WARNING.
          const char *names[] = {OH_EVENT_APP_FREEZE_WARNING};
          // Subscribe to events of interest. Here, a system event is subscribed to.
          OH_HiAppEvent_SetAppEventFilter(appFreezeWarningWatcherT, DOMAIN_OS, 0, names, 1);
          // Set the implemented callback function. The callback is triggered only when the conditions set by OH_HiAppEvent_SetTriggerCondition are met.
          OH_HiAppEvent_SetWatcherOnTrigger(appFreezeWarningWatcherT, OnTriggerAppFreezeWarning);
          // Set the conditions for triggering the subscription callback. Here, the onTrigger callback is triggered when the number of new event records reaches 1.
          OH_HiAppEvent_SetTriggerCondition(appFreezeWarningWatcherT, 1, 0, 0);
          // Start listening for subscribed events with the watcher.
          OH_HiAppEvent_AddWatcher(appFreezeWarningWatcherT);
          return {};
      }
      ```

6. Register **RegisterWatcher** as an ArkTS API.

   Edit **entry > src > main > cpp > napi_init.cpp** in the project and register **RegisterAppFreezeWarningReceiveWatcher** and **RegisterAppFreezeWarningTriggerWatcher** as ArkTS APIs:
   
   <!-- @[AppFreezeWarning_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           // ...
           { "registerAppFreezeWarningReceiveWatcher", nullptr, RegisterAppFreezeWarningReceiveWatcher,
               nullptr, nullptr, nullptr, napi_default, nullptr },
           { "registerAppFreezeWarningTriggerWatcher", nullptr, RegisterAppFreezeWarningTriggerWatcher,
               nullptr, nullptr, nullptr, napi_default, nullptr },
           // ...
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   ```

   Edit **entry > src > main > cpp > types > libentry > Index.d.ts** in the project and define the ArkTS APIs:
   
   <!-- @[AppFreezeWarning_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->
   
   ``` TypeScript
   export const registerAppFreezeWarningReceiveWatcher: () => void;
   export const registerAppFreezeWarningTriggerWatcher: () => void;
   ```

7. Edit **entry > src > main > ets > entryability > EntryAbility.ets** in the project and add API calls to **onCreate()**.

   <!-- @[AppFreezeWarning_Call_Capi_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // Add the API call in the onCreate() function.
   // Register the system event watcher at startup.
   testNapi.registerAppFreezeWarningReceiveWatcher();
   testNapi.registerAppFreezeWarningTriggerWatcher();
   ```

8. Edit the **Index.ets** file under **entry > src > main > ets > pages** in the project to add a button that triggers the app freeze warning event. The sample code is as follows:

   <!-- @[AppFreezeWarning_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   Button("appFreezeWarning")
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       // Construct an appFreezeWarning scenario in the button click function to trigger an App Freeze warning event.
       const t = Date.now();
       while (Date.now() - t <= 6500) {}
     })
   ```

9. Run the app project in DevEco Studio, and then click the **appFreezeWarning** button in the app UI to trigger an app freeze warning event.

### Verifying That the Observer Has Received App Freeze Warning Events

After about one minute, the **Log** window displays the logs generated when the system event data is processed:

``` Text
HiAppEvent eventInfo.domain=OS
HiAppEvent eventInfo.name=APPFREEZE_WARNING
HiAppEvent eventInfo.eventType=1
HiAppEvent eventInfo.params.time=1776946769389
HiAppEvent eventInfo.params.foreground=1
HiAppEvent eventInfo.params.app_running_unique_id=382145346984526931478
HiAppEvent eventInfo.params.bundle_version=1.0.0
HiAppEvent eventInfo.params.bundle_version_code=1000000
HiAppEvent eventInfo.params.bundle_name=com.example.myapplication
HiAppEvent eventInfo.params.process_name=com.example.myapplication
HiAppEvent eventInfo.params.pid=1587
HiAppEvent eventInfo.params.uid=20010043
HiAppEvent eventInfo.params.exception={""message":"App main thread is not response!Main handler dump start time: 2026-04-23 20:19:28.903","name":"THREAD_BLOCK_3S"}
HiAppEvent eventInfo.params.hilog.size=6
HiAppEvent eventInfo.params.event_handler.size=16
HiAppEvent eventInfo.params.peer_binder.size=0
HiAppEvent eventInfo.params.threads.size=28
HiAppEvent eventInfo.params.memory={"rss":161080,"sys_avail_mem":1361464,"sys_free_mem":796232,"sys_total_mem":1992340,"vm_heap_total_size":"9961472","vm_heap_used_size":"7596424","vss":56960692}
HiAppEvent eventInfo.params.process_life_time=18
```


### Removing and Destroying the Event Watcher

1. Remove the event watcher.

   <!-- @[AppFreezeWarning_RemoveWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value RemoveAppFreezeWarningWatcher(napi_env env, napi_callback_info info)
   {
       // Stop the watcher from listening for events.
       OH_HiAppEvent_RemoveWatcher(appFreezeWarningWatcherR);
       OH_HiAppEvent_RemoveWatcher(appFreezeWarningWatcherT);
       return {};
   }
   ```

2. Destroy the event watcher.

   <!-- @[AppFreezeWarning_DestroyWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value DestroyAppFreezeWarningWatcher(napi_env env, napi_callback_info info)
   {
       // Destroy the created watcher and set systemEventWatcher to nullptr.
       OH_HiAppEvent_DestroyWatcher(appFreezeWarningWatcherR);
       OH_HiAppEvent_DestroyWatcher(appFreezeWarningWatcherT);
       appFreezeWarningWatcherR = nullptr;
       appFreezeWarningWatcherT = nullptr;
       return {};
   }
   ```