# Subscribing to Application Killed Events (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=bbac2265b5354ed331c839e017d611d73c2d5f39 translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T07:39:08.000Z nl=1 -->

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

1. In the **entry/src/main/ets/entryability/EntryAbility.ets** file of the project, import the dependent modules.

   ```ts
   import { hiAppEvent } from '@kit.PerformanceAnalysisKit';
   ```

2. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, add a watcher in **onCreate()** to subscribe to system events. The sample code is as follows:

   ```ts
   hiAppEvent.addWatcher({
     // You can customize the watcher name, which the system uses to identify different watchers.
     name: "watcher",
     // You can subscribe to system events that you are interested in. Here, the application killed event is subscribed to.
     appEventFilters: [
       {
         domain: hiAppEvent.domain.OS,
         names: [hiAppEvent.event.APP_KILLED]
       }
     ],
     // You can implement the subscription real-time callback to process the subscribed event data as needed.
     onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
       hilog.info(0x0000, 'testTag', `HiAppEvent onReceive: domain=${domain}`);
       for (const eventGroup of appEventGroups) {
         // You can distinguish different system events by the event name in the event group.
         hilog.info(0x0000, 'testTag', `HiAppEvent eventName=${eventGroup.name}`);
         for (const eventInfo of eventGroup.appEventInfos) {
           // You can process the event data in the event group as needed. Here, the event data is printed in the log.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.domain=${eventInfo.domain}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.name=${eventInfo.name}`);
           // Obtain the timestamp when the application is killed.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.time=${eventInfo.params['time']}`);
           // Obtain the foreground and background status of the application when the killed event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.foreground=${eventInfo.params['foreground']}`);
           // Obtain the cause of the application killed event.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.reason=${eventInfo.params['reason']}`);
           // Obtain the ID of the process that initiates termination.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.calling_pid=${eventInfo.params['calling_pid']}`);
           // Obtain the name of the process that initiates termination.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.calling_process_name=${eventInfo.params['calling_process_name']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.app_running_unique_id=${eventInfo.params['app_running_unique_id']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version=${eventInfo.params['bundle_version']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.last_exit_detail_info=${JSON.stringify(eventInfo.params['last_exit_detail_info'])}`);
         }
       }
     }
   });
   ```

3. Edit the **napi_init.cpp** file and add the following code to implement the fault-injection functionality in C++.

   ```C++
   #include <thread>
   
   static void NativeLeak()
   {
       constexpr int leak_size_per_time = 500000;
       while (true) {
           char *p = (char *)malloc(leak_size_per_time + 1);
           if (!p) {
               break;
           }
           memset(p, 'a', leak_size_per_time);
           std::this_thread::sleep_for(std::chrono::milliseconds(10));
       }
   }
   
   static napi_value Leak(napi_env env, napi_callback_info info) {
    std::thread t1(NativeLeak);
    t1.detach();
       return {};
   }
   ```

4. In the **napi_init.cpp** file, register **Leak** as an ArkTS API.

   ```c++
   static napi_value Init(napi_env env, napi_value exports)
   {
       napi_property_descriptor desc[] = {
           { "leak", nullptr, Leak, nullptr, nullptr, nullptr, napi_default, nullptr }, // Add this line.
       };
       napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
       return exports;
   }
   ```

5. In the **index.d.ts** file, define the ArkTS API.

   ```ts
   export const leak: () => void;
   ```

6. In the **entry/src/main/ets/pages/Index.ets** file, add the **OnClick** function under **build()** and call the **Leak** API.

   ```ts
   import { hilog } from '@kit.PerformanceAnalysisKit';
   import testNapi from 'libentry.so';
   
   const DOMAIN = 0x0000;
   
   @Entry
   @Component
   struct Index {
     @State message: string = 'Start To Leak';
   
     build() {
       Row() {
         Column() {
           Text(this.message)
             .fontSize($r('app.float.page_text_font_size'))
             .fontWeight(FontWeight.Bold)
             .onClick(() => {
               if (this.message != 'Leaking') {
                 this.message = 'Leaking';
                 hilog.info(DOMAIN, 'testTag', 'Start leaking');
                 testNapi.leak();
               }
             })
         }
         .width('100%')
       }
       .height('100%')
     }
   }
   ```

7. Click the **Run** button in DevEco Studio to run the project. Click **Start To Leak**, and wait for 2 to 3 minutes until **RssThresholdKiller** is triggered.

8. After the application is killed, open the application again. The killed event is reported, and the system calls **onReceive()**. You can view the following event information in the **Log** window.

   Sample stack of the application killed event:

   ```text
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
