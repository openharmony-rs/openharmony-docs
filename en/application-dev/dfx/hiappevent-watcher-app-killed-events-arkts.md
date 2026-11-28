# Subscribing to Application Killed Events (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=8c80ccbb09d5b92143b13c87f24e3198a47da7da translatedAt=2026-11-28T03:12:44.833Z nl=2 -->

## Event Specifications

For details, see [Application Killed Event Overview](./hiappevent-watcher-app-killed-events.md).

## Available APIs

For details about how to use the APIs, see [@ohos.hiviewdfx.hiAppEvent (Application Event Logging)](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

| Name                                             | Description                                        |
| --------------------------------------------------- | -------------------------------------------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | Adds a watcher to subscribe to the application event.|
| removeWatcher(watcher: Watcher): void               | Removes a watcher to unsubscribe from the application event.|

## How to Develop

To ensure smooth reception of event callbacks during development, you are advised to adopt the following approach: create a new Native C++ project, implement the subscription in ArkTS code, and use fault injection code in C++ to construct faults that trigger `APP_KILLED` events.

1. In the **entry/src/main/ets/entryability/EntryAbility.ets** file of the project, import the dependent modules:

   <!-- @[AppKillEvent_ArkTS_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, add a watcher in **onCreate()** to subscribe to system events. The sample code is as follows:

   <!-- @[AppKillEvent_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   hiAppEvent.addWatcher({
     // Set the watcher name. The system identifies different watchers based on their names.
     name: 'appKilledWatcher',
     // You can subscribe to system events that you are interested in. Here, the application killed event is subscribed to.
     appEventFilters: [
       {
         domain: hiAppEvent.domain.OS,
         names: [hiAppEvent.event.APP_KILLED]
       }
     ],
     // Implement a callback for the registered system event so that you can apply custom processing to the event data obtained.
     onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
       hilog.info(0x0000, 'testTag', `HiAppEvent onReceive: domain=${domain}`);
       for (const eventGroup of appEventGroups) {
         // The event name uniquely identifies a system event.
         hilog.info(0x0000, 'testTag', `HiAppEvent eventName=${eventGroup.name}`);
         for (const eventInfo of eventGroup.appEventInfos) {
           // Apply custom processing to the event data obtained, for example, print the event data in the log.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.domain=${eventInfo.domain}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.name=${eventInfo.name}`);
           // Obtain the timestamp when the application is killed.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.time=${eventInfo.params['time']}`);
           // Obtain the foreground and background status of the application when the killed event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.foreground=${eventInfo.params['foreground']}`);
           // Obtain the cause of the application killed event.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.reason=${eventInfo.params['reason']}`);
           // Obtain the ID of the process that initiates process termination.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.calling_pid=${eventInfo.params['calling_pid']}`);
           // Obtain the name of the process that initiates process termination.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.calling_process_name=${eventInfo.params['calling_process_name']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.app_running_unique_id=${eventInfo.params['app_running_unique_id']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version=${eventInfo.params['bundle_version']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.last_exit_detail_info=${JSON.stringify(eventInfo.params['last_exit_detail_info'])}`);
         }
       }
     }
   });
   ```

3. The following fault injection functionality requires C++ code. Edit **entry > src > main > cpp > napi_init.cpp** in the project and add the header files:
   
   <!-- @[AppKillEvent_NativeLeak_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   #include <thread>
   ```

4. Edit **entry > src > main > cpp > napi_init.cpp** in the project and add the **NativeLeak** and **Leak** methods:

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

5. Edit **entry > src > main > cpp > napi_init.cpp** in the project and register **Leak** as an ArkTS API:

   <!-- @[AppKillEvent_ArkTS_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
   
   ``` C++
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           // ...
           { "leak", nullptr, Leak, nullptr, nullptr, nullptr, napi_default, nullptr},
           // ...
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   ```

6. Edit **entry > src > main > cpp > types > libentry > Index.d.ts** in the project and define the ArkTS API:

   <!-- @[AppKillEvent_ArkTS_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->
   
   ``` TypeScript
   export const leak: () => void;
   ```

7. Edit **entry > src > main > ets > pages > Index.ets** in the project and add the **@State** variable:

   <!-- @[AppKillEvent_ArkTS_State](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   @State message: string = 'Start To Leak';
   ```

8. In the **entry/src/main/ets/pages/Index.ets** file, add the **OnClick** function under **build()** and call the **Leak** API:

   <!-- @[AppKillEvent_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   Button(this.message)
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       if (this.message != 'Leaking') {
         this.message = 'Leaking';
         hilog.info(0x0000, 'testTag', 'Start leaking');
         testNapi.leak();
       }
     })
   ```

9. Click the **Run** button in DevEco Studio to run the project. Click **Start To Leak**, and wait for 2 to 3 minutes until **RssThresholdKiller** is triggered.

10. After the application is killed, open the application again. The killed event is reported, and the system calls **onReceive()**. You can view the following event information in the **Log** window.

    Sample stack of the application killed event:

    ``` Text
    HiAppEvent eventInfo.domain=OS
    HiAppEvent eventInfo.name=APP_KILLED
    HiAppEvent eventInfo.params.time=1792739581978
    HiAppEvent eventInfo.params.reason="RssThresholdKiller"
    HiAppEvent eventInfo.params.foreground=true
    HiAppEvent eventInfo.params.calling_pid="43"
    HiAppEvent eventInfo.params.calling_process_name="wk:0/0/1/12"
    HiAppEvent eventInfo.params.app_running_unique_id=8778602711597370439
    HiAppEvent eventInfo.params.bundle_version=1.0.1
    HiAppEvent eventInfo.params.last_exit_detail_info={"exit_msg":"","kill_reason":"RssThresholdKiller","pid":"17248","process_name":"com.example.dfx_test","process_state":"2","pss":"227764","rss":"227764","timestamp":"1792739581947","uid":"20020207"}
    ```