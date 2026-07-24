# Subscribing to App Freeze Warning Events (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=abb2cbc3c0ee7701da88cfed86a07b11347a25be translatedAt=2026-07-08T03:43:49.372Z pushedAt=2026-07-08T06:42:20.978Z -->

## Overview

This section describes how to use the ArkTS APIs provided by HiAppEvent to subscribe to app freeze warning events. For detailed usage instructions of the APIs (parameter constraints, value ranges, etc.), see [@ohos.hiviewdfx.hiAppEvent](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

## Available APIs

| Name | Description |
| -------- | -------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | Adds an app event watcher to subscribe to app events. |
| removeWatcher(watcher: Watcher): void | Removes an app event watcher to unsubscribe from app events. |

## How to Develop

### Adding an Event Watcher

The following uses subscribing to app freeze warning events as an example to illustrate the development procedure.

1. Create an ArkTS app project and edit the **EntryAbility.ets**  file under **entry > src > main > ets > entryability** in the project to import the dependency modules. The following is the sample code:

   ```ts
   import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
   ```

2. Edit the **EntryAbility.ets** file under **entry > src > main > ets > entryability** in the project to add the subscription to system events in the **onCreate** function. The following is the sample code:

   ```ts
   hiAppEvent.addWatcher({
     // Customize the watcher name, which is used by the system to identify different watchers.
     name: "watcher",
     // Subscribe to system events of interest. Here, the app freeze warning event is subscribed.
     appEventFilters: [
       {
         domain: hiAppEvent.domain.OS,
         names: [hiAppEvent.event.appFreezeWarning]
       }
     ],
     // Implement a real-time event callback to process subscribed event data as needed.
     onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
       hilog.info(0x0000, 'testTag', `HiAppEvent onReceive: domain=${domain}`);
       for (const eventGroup of appEventGroups) {
         // You can distinguish different system events based on the event name in the event group.
         hilog.info(0x0000, 'testTag', `HiAppEvent eventName=${eventGroup.name}`);
         for (const eventInfo of eventGroup.appEventInfos) {
           // Process the event data in the event group. Here, the event data is printed in the log.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.domain=${eventInfo.domain}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.name=${eventInfo.name}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.eventType=${eventInfo.eventType}`);
           // Timestamp when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.time=${eventInfo.params['time']}`);
           // Foreground/Background status of the app when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.foreground=${eventInfo.params['foreground']}`);
           // Unique correlation ID of the app when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.app_running_unique_id=${eventInfo.params['app_running_unique_id']}`);
           // Version information of the app when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version=${eventInfo.params['bundle_version']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version_code=${eventInfo.params['bundle_version_code']}`);
           // Bundle name of the app when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_name=${eventInfo.params['bundle_name']}`);
           // Process name of the app when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.process_name=${eventInfo.params['process_name']}`);
           // Process ID of the app when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.pid=${eventInfo.params['pid']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.uid=${eventInfo.params['uid']}`);
           // Exception type and cause of the app freeze warning event.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.exception=${JSON.stringify(eventInfo.params['exception'])}`);
           // Log information when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.hilog.size=${eventInfo.params['hilog'].length}`);
           // Unprocessed messages in the main thread when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.event_handler.size=${eventInfo.params['event_handler'].length}`);
           // Synchronous binder call information when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.peer_binder.size=${eventInfo.params['peer_binder'].length}`);
           // Full thread call stack when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.threads.size=${eventInfo.params['threads'].length}`);
           // Memory information when the app freeze warning event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.memory=${JSON.stringify(eventInfo.params['memory'])}`);
           // Lifetime of the process in which the app freeze warning occurred.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.process_life_time=${eventInfo.params['process_life_time']}`);
         }
       }
     }
   });
   ```

3. Edit the **Index.ets** file under **entry > src > main > ets > pages** in the project to add a button that triggers the app freeze warning event. The sample code is as follows:

   ```ts
     @Entry
     @Component
     struct Index {
       build() {
         RelativeContainer() {
           Column() {
             Button("appFreezeWarning", { stateEffect:true, type: ButtonType.Capsule})
               .width('75%')
               .height(50)
               .margin(15)
               .fontSize(20)
               .fontWeight(FontWeight.Bold)
               .onClick(() => {
                // Simulate an app freeze to trigger an app freeze warning event.
                 const t = Date.now();
                 while (Date.now() - t <= 6500) {}
               })
           }.width('100%')
         }
         .height('100%')
         .width('100%')
       }
     }
   ```

4. Run the app project in DevEco Studio, and then click the **appFreezeWarning** button in the app UI to trigger an app freeze warning event.

### Verifying That the Observer Has Received App Freeze Warning Events

After about one minute, the **Log** window displays the logs generated when the system event data is processed:

```text
HiAppEvent onReceive: domain=OS
HiAppEvent eventName=APPFREEZE_WARNING
HiAppEvent eventInfo.domain=OS
HiAppEvent eventInfo.name=APPFREEZE_WARNING
HiAppEvent eventInfo.eventType=1
HiAppEvent eventInfo.params.time=1776946769389
HiAppEvent eventInfo.params.foreground=true
HiAppEvent eventInfo.params.app_running_unique_id=215456512336951247
HiAppEvent eventInfo.params.bundle_version=1.0.0
HiAppEvent eventInfo.params.bundle_version_code=1000000
HiAppEvent eventInfo.params.bundle_name=com.example.myapplication
HiAppEvent eventInfo.params.process_name=com.example.myapplication
HiAppEvent eventInfo.params.pid=39067
HiAppEvent eventInfo.params.uid=20010043
HiAppEvent eventInfo.params.exception={"message":"App main thread is not response!Main handler dump start time: 2026-04-23 20:19:28.903","name":"THREAD_BLOCK_3S"}
HiAppEvent eventInfo.params.hilog.size=77
HiAppEvent eventInfo.params.event_handler.size=6
HiAppEvent eventInfo.params.peer_binder.size=0
HiAppEvent eventInfo.params.threads.size=28
HiAppEvent eventInfo.params.memory={"rss":161080,"sys_avail_mem":1361464,"sys_free_mem":796232,"sys_total_mem":1992340,"vm_heap_total_size":"9961472","vm_heap_used_size":"7596424","vss":56960692}
HiAppEvent eventInfo.params.process_life_time=18
```