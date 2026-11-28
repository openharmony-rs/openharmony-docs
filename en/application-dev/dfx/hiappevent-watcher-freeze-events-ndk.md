# Subscribing to Application Freeze Events (C/C++)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=7ee11c1f0301e6100e1f26dcd0b3d3ad99aef3fb translatedAt=2026-11-28T03:12:44.837Z nl=2 -->

## Overview

This section describes how to use the C/C++ APIs provided by HiAppEvent to subscribe to app freeze events. For detailed API usage instructions (parameter constraints, value ranges, etc.), refer to [hiappevent.h](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md).

## Available APIs

| API| Description|
| -------- | -------- |
| int OH_HiAppEvent_AddWatcher(HiAppEvent_Watcher \*watcher) | Adds a watcher to listen for application events.|
| int OH_HiAppEvent_RemoveWatcher(HiAppEvent_Watcher \*watcher) | Removes a watcher to unsubscribe from application events.|

## How to Develop

### Adding an Event Watcher

The following walks you through on how to subscribe to the application freeze events.

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

3. Edit the **entry > src > main > cpp > CMakeLists.txt** file in the project to add source files and dynamic libraries.

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
   # Add libhiappevent_ndk.z.so and libhilog_ndk.z.so (log output).
   target_link_libraries(entry PUBLIC libace_napi.z.so libhilog_ndk.z.so libhiappevent_ndk.z.so)
   # Add the third-party library dependency libjsoncpp.so to parse JSON strings in subscribed events.
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

   - Watcher of the **onReceive** type:

      Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to define the methods related to the watcher of the **onReceive** type:

      <!-- @[FreezeEvent_OnReceive](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
      
      ``` C++
      // Define a variable to cache the pointer of the created watcher.
      static HiAppEvent_Watcher *systemReceiveFreezeWatcher;
      
      // Extract logging of additional parameters into a separate function because FreezeEventOutput exceeds the 50-line limit.
      static void OutputFreezeEventExtraParams(Json::Value params, Json::FastWriter writer)
      {
          auto memory = writer.write(params["memory"]);
          auto externalLog = writer.write(params["external_log"]);
          auto logOverLimit = params["log_over_limit"].asBool();
          auto handleSize3s = params["event_handler_size_3s"].asString();
          auto handleSize6s = params["event_handler_size_6s"].asString();
          auto externalCallbackLog = params["external_callback_log"].asString();
          auto applicationGCInfo = params["application_gc_info"].asString();
          auto applicationIOInfo = params["application_io_info"].asString();
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.memory=%{public}s", memory.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.external_log=%{public}s", externalLog.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.log_over_limit=%{public}d", logOverLimit);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler_3s.size=%{public}s",
              handleSize3s.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler_6s.size=%{public}s",
              handleSize6s.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.external_callback_log=%{public}s",
              externalCallbackLog.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.application_gc_info=%{public}s",
              applicationGCInfo.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.application_io_info=%{public}s",
              applicationIOInfo.c_str());
      }
      
      // Extract log output into a separate function because OnReceiveFreezeEvent exceeds the 50-line limit.
      static void FreezeEventOutput(Json::Value params, Json::FastWriter writer)
      {
          auto time = params["time"].asInt64();
          auto foreground = params["foreground"].asBool();
          auto appRunningUniqueId = params["app_running_unique_id"].asString();
          auto bundleVersion = params["bundle_version"].asString();
          auto bundleName = params["bundle_name"].asString();
          auto processName = params["process_name"].asString();
          auto pid = params["pid"].asInt();
          auto uid = params["uid"].asInt();
          auto uuid = params["uuid"].asString();
          auto exception = writer.write(params["exception"]);
          auto hilogSize = params["hilog"].size();
          auto handleSize = params["event_handler"].size();
          auto peerBindSize = params["peer_binder"].size();
          auto threadSize = params["threads"].size();
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.time=%{public}lld", time);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.foreground=%{public}d", foreground);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.app_running_unique_id=%{public}s",
              appRunningUniqueId.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version=%{public}s", bundleVersion.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_name=%{public}s", bundleName.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.process_name=%{public}s", processName.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.pid=%{public}d", pid);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uid=%{public}d", uid);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uuid=%{public}s", uuid.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.exception=%{public}s", exception.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.hilog.size=%{public}d", hilogSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler.size=%{public}d", handleSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.peer_binder.size=%{public}d", peerBindSize);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.threads.size=%{public}d", threadSize);
          OutputFreezeEventExtraParams(params, writer);
      }
      
      static void HandleFreezeEvent(const struct HiAppEvent_AppEventInfo &appEventInfos)
      {
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.domain=%{public}s", appEventInfos.domain);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.name=%{public}s", appEventInfos.name);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.eventType=%{public}d", appEventInfos.type);
          if (strcmp(appEventInfos.domain, DOMAIN_OS) == 0 &&
              strcmp(appEventInfos.name, EVENT_APP_FREEZE) == 0) {
              Json::Value params;
              Json::Reader reader(Json::Features::strictMode());
              Json::FastWriter writer;
              if (reader.parse(appEventInfos.params, params)) {
                  FreezeEventOutput(params, writer);
              }
          }
      }
      
      static void OnReceiveFreezeEvent(const char *domain, const struct HiAppEvent_AppEventGroup *appEventGroups,
          uint32_t groupLen)
      {
          for (int i = 0; i < groupLen; ++i) {
              for (int j = 0; j < appEventGroups[i].infoLen; ++j) {
                  HandleFreezeEvent(appEventGroups[i].appEventInfos[j]);
              }
          }
      }
      
      static napi_value RegisterFreezeWatcherR(napi_env env, napi_callback_info info)
      {
          // Set the watcher name. The system identifies different watchers based on their names.
          systemReceiveFreezeWatcher = OH_HiAppEvent_CreateWatcher("onReceiveFreezeWatcher");
          // Set the event to watch to EVENT_APP_FREEZE.
          const char *names[] = {EVENT_APP_FREEZE};
          // Add the events to watch, for example, system events.
          OH_HiAppEvent_SetAppEventFilter(systemReceiveFreezeWatcher, DOMAIN_OS, 0, names, 1);
          // Set the implemented callback function. When the watcher receives an event, the OnReceive callback is triggered immediately.
          OH_HiAppEvent_SetWatcherOnReceive(systemReceiveFreezeWatcher, OnReceiveFreezeEvent);
          // Add a watcher to listen for the specified event.
          OH_HiAppEvent_AddWatcher(systemReceiveFreezeWatcher);
          return {};
      }
      ```

   - Watcher of the **onTrigger** type:

      Edit the **napi_init.cpp** file under **entry > src > main > cpp** in the project to define the functions related to the watcher of the **onTrigger** type:

      <!-- @[FreezeEvent_OnTrigger](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
      
      ``` C++
      // Define a variable to cache the pointer of the created watcher.
      static HiAppEvent_Watcher *systemTriggerFreezeWatcher;
      
      // Extract logging of additional parameters into a separate function because OnFreezeEventOutput exceeds the 50-line limit.
      static void OutputOnFreezeEventExtraParams(Json::Value params, Json::FastWriter writer)
      {
          auto memory = writer.write(params["memory"]);
          auto externalLog = writer.write(params["external_log"]);
          auto logOverLimit = params["log_over_limit"].asBool();
          auto handleSize3s = params["event_handler_size_3s"].asString();
          auto handleSize6s = params["event_handler_size_6s"].asString();
          auto externalCallbackLog = params["external_callback_log"].asString();
          auto applicationGCInfo = params["application_gc_info"].asString();
          auto applicationIOInfo = params["application_io_info"].asString();
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.memory=%{public}s", memory.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.external_log=%{public}s", externalLog.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.log_over_limit=%{public}d", logOverLimit);
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler_3s.size=%{public}s",
              handleSize3s.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler_6s.size=%{public}s",
              handleSize6s.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.external_callback_log=%{public}s",
              externalCallbackLog.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.application_gc_info=%{public}s",
              applicationGCInfo.c_str());
          OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.application_io_info=%{public}s",
              applicationIOInfo.c_str());
      }
      
      static void OnFreezeEventOutPut(std::string domain, std::string name, Json::Value eventInfo, Json::FastWriter writer)
      {
          if (domain ==  DOMAIN_OS && name == EVENT_APP_FREEZE) {
              auto time = eventInfo["time"].asInt64();
              auto foreground = eventInfo["foreground"].asBool();
              auto appRunningUniqueId = eventInfo["app_running_unique_id"].asString();
              auto bundleVersion = eventInfo["bundle_version"].asString();
              auto bundleName = eventInfo["bundle_name"].asString();
              auto processName = eventInfo["process_name"].asString();
              auto pid = eventInfo["pid"].asInt();
              auto uid = eventInfo["uid"].asInt();
              auto uuid = eventInfo["uuid"].asString();
              auto exception = writer.write(eventInfo["exception"]);
              auto hilogSize = eventInfo["hilog"].size();
              auto handleSize = eventInfo["event_handler"].size();
              auto peerBindSize = eventInfo["peer_binder"].size();
              auto threadSize = eventInfo["threads"].size();
              auto process_life_time = eventInfo["process_life_time"].asString();
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.time=%{public}lld", time);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.foreground=%{public}d", foreground);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.app_running_unique_id=%{public}s",
                  appRunningUniqueId.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_version=%{public}s",
                  bundleVersion.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.bundle_name=%{public}s",
                  bundleName.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.process_name=%{public}s",
                  processName.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.pid=%{public}d", pid);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uid=%{public}d", uid);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.uuid=%{public}s", uuid.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.exception=%{public}s", exception.c_str());
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.hilog.size=%{public}d", hilogSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.event_handler.size=%{public}d", handleSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.peer_binder.size=%{public}d", peerBindSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.threads.size=%{public}d", threadSize);
              OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.params.process_life_time=%{public}s",
                  process_life_time.c_str());
              OutputOnFreezeEventExtraParams(eventInfo, writer);
          }
      }
      
      // Implement the callback function used to return the listened events. The content pointed to by the events pointer is valid only in this function.
      static void OnFreezeTake(const char *const *events, uint32_t eventLen)
      {
          Json::Reader reader(Json::Features::strictMode());
          Json::FastWriter writer;
          for (int i = 0; i < eventLen; ++i) {
              Json::Value eventInfo;
              if (reader.parse(events[i], eventInfo)) {
                  auto domain =  eventInfo["domain_"].asString();
                  auto name = eventInfo["name_"].asString();
                  auto type = eventInfo["type_"].asInt();
                  OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.domain=%{public}s", domain.c_str());
                  OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.name=%{public}s", name.c_str());
                  OH_LOG_INFO(LogType::LOG_APP, "HiAppEvent eventInfo.eventType=%{public}d", type);
                  // Process the freeze event.
                  OnFreezeEventOutPut(domain, name, eventInfo, writer);
              }
          }
      }
      
      // Implement the subscription callback function to apply custom processing to the obtained event logging data.
      static void OnTriggerFreezeEvent(int row, int size)
      {
          // After the callback is received, obtain the specified number of received events.
          OH_HiAppEvent_TakeWatcherData(systemTriggerFreezeWatcher, row, OnFreezeTake);
      }
      
      static napi_value RegisterFreezeWatcherT(napi_env env, napi_callback_info info)
      {
          // Set the watcher name. The system identifies different watchers based on their names.
          systemTriggerFreezeWatcher = OH_HiAppEvent_CreateWatcher("OnTriggerFreezeEventWatcher");
          // Set the event to watch to EVENT_APP_FREEZE.
          const char *names[] = {EVENT_APP_FREEZE};
          // Add the events to watch, for example, system events.
          OH_HiAppEvent_SetAppEventFilter(systemTriggerFreezeWatcher, DOMAIN_OS, 0, names, 1);
          // Set the implemented callback function. The callback function will be triggered when the conditions set by OH_HiAppEvent_SetTriggerCondition are met.
          OH_HiAppEvent_SetWatcherOnTrigger(systemTriggerFreezeWatcher, OnTriggerFreezeEvent);
          // Set the conditions for triggering the subscription callback. For example, trigger this onTrigger callback when the number of new event logs is 1.
          OH_HiAppEvent_SetTriggerCondition(systemTriggerFreezeWatcher, 1, 0, 0);
          // Add a watcher to listen for the specified event.
          OH_HiAppEvent_AddWatcher(systemTriggerFreezeWatcher);
          return {};
      }
      ```

6. Register **RegisterFreezeWatcherR** and **RegisterFreezeWatcherT** as ArkTS APIs.

   Edit **entry > src > main > cpp > napi_init.cpp** in the project and register **RegisterFreezeWatcherR** and **RegisterFreezeWatcherT** as ArkTS APIs:

   <!-- @[FreezeEvent_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           // ...
           { "RegisterFreezeWatcherR", nullptr, RegisterFreezeWatcherR, nullptr, nullptr, nullptr, napi_default, nullptr },
           { "RegisterFreezeWatcherT", nullptr, RegisterFreezeWatcherT, nullptr, nullptr, nullptr, napi_default, nullptr },
           // ...
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   ```

   Edit **entry > src > main > cpp > types > libentry > Index.d.ts** in the project and define the ArkTS APIs:

   <!-- @[Freeze_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->
   
   ``` TypeScript
   export const RegisterFreezeWatcherR: () => void;
   export const RegisterFreezeWatcherT: () => void;
   ```

7. Edit the **EntryAbility.ets** file under **entry > src > main > ets > entryability** in the project to add API calls in the `onCreate()` function.

   <!-- @[Freeze_Event_Call_Capi_Function](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // Add the API to onCreate().
   // Register the system event watcher at startup.
   testNapi.RegisterFreezeWatcherR();
   testNapi.RegisterFreezeWatcherT();
   ```

8. Edit **entry > src > main > ets > pages > Index.ets** in the project and add a button. In its **onClick** handler, simulate an unresponsive application to trigger an application freeze event. The sample code is as follows:

   <!-- @[AppfreezeEvent_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   Button('AppFreeze')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       // Construct a freeze scenario in onClick() to trigger an application freeze event.
       setTimeout(() => {
         let t = Date.now();
         while (Date.now() - t <= 15000) {}
       }, 5000);
     })
   ```

9. In DevEco Studio, click the **Run** button to run the project. Then, click the **appFreeze** button in the app UI to trigger an app freeze event.

### Verifying That the Watcher Has Subscribed to App Freeze Events

1. The application crashes. After restarting the application, you can view the following event information in the **Log** window.

   ``` Text
   HiAppEvent eventInfo.domain=OS
   HiAppEvent eventInfo.name=APP_FREEZE
   HiAppEvent eventInfo.eventType=1
   HiAppEvent eventInfo.params.time=1502049167732
   HiAppEvent eventInfo.params.foreground=1
   HiAppEvent eventInfo.params.app_running_unique_id=382145346984526931478
   HiAppEvent eventInfo.params.bundle_version=1.0.0
   HiAppEvent eventInfo.params.bundle_name=com.example.myapplication
   HiAppEvent eventInfo.params.process_name=com.example.myapplication
   HiAppEvent eventInfo.params.pid=1587
   HiAppEvent eventInfo.params.uid=20010043
   HiAppEvent eventInfo.params.uuid=a78a23b20f3dd9730f18a5cfa2304deac1104ac4086755c4a59cf7c72d414e2e
   HiAppEvent eventInfo.params.exception={"message":"App main thread is not response!","name":"THREAD_BLOCK_6S"}
   HiAppEvent eventInfo.params.hilog.size=6
   HiAppEvent eventInfo.params.event_handler.size=16
   HiAppEvent eventInfo.params.event_handler_3s.size=15
   HiAppEvent eventInfo.params.event_handler_6s.size=16
   HiAppEvent eventInfo.params.peer_binder.size=0
   HiAppEvent eventInfo.params.threads.size=28
   HiAppEvent eventInfo.params.memory={"pss":0,"rss":0,"sys_avail_mem":1326520,"sys_free_mem":940588,"sys_total_mem":1992340,"vm_heap_total_size":"9961472","vm_heap_used_size":"7596424","vss":0}
   HiAppEvent eventInfo.params.external_log=["/data/storage/el2/log/hiappevent/APP_FREEZE_1502049185239_1587.log"]
   HiAppEvent eventInfo.params.log_over_limit=0
   HiAppEvent eventInfo.params.process_life_time=18
   HiAppEvent eventInfo.params.external_callback_log=THREAD_BLOCK_3S:log3s THREAD_BLOCK_6S:log6s
   ```

2. If the application fails to start or remains unstarted for a long time, you can delay the event notification by referring to [Using FaultLogExtensionAbility to Subscribe to Events](./fault-log-extension-app-events-arkts.md).

### Removing and Destroying an Event Watcher

1. Remove the event watcher.

   <!-- @[FreezeEvent_RemoveWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value RemoveWatcherFreeze(napi_env env, napi_callback_info info)
   {
       // Stop the watcher from listening for freeze events.
       OH_HiAppEvent_RemoveWatcher(systemReceiveFreezeWatcher);
       OH_HiAppEvent_RemoveWatcher(systemTriggerFreezeWatcher);
       return {};
   }
   ```

2. Destroy the event watcher.

   <!-- @[FreezeEvent_DestroyWatcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value DestroyWatcherFreeze(napi_env env, napi_callback_info info)
   {
       // Destroy the watcher and set the watcher pointer to nullptr.
       OH_HiAppEvent_DestroyWatcher(systemReceiveFreezeWatcher);
       OH_HiAppEvent_DestroyWatcher(systemTriggerFreezeWatcher);
       systemReceiveFreezeWatcher = nullptr;
       systemTriggerFreezeWatcher = nullptr;
       return {};
   }
   ```