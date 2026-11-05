# Subscribing to Main Thread Jank Events (ArkTS)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=b3002ba9e170e60c2ca2ddd623c2ab4f4030ff0d translatedAt=2026-11-05T06:16:33.940Z pushedAt=2026-09-29T10:11:08.085Z nl=1 -->

## Overview

This document describes how to use the ArkTS APIs provided by HiAppEvent to subscribe to main thread jank events. For detailed usage instructions (parameter constraints, value ranges, etc.) of the APIs, see [@ohos.hiviewdfx.hiAppEvent](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

## Available APIs

| API| Description|
| -------- | -------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | Adds a watcher to listen for application events.|
| removeWatcher(watcher: Watcher): void | Removes a watcher to unsubscribe from application events.|

## How to Develop

### Adding an Event Watcher

The following walks you through on how to subscribe to the main thread jank event.

1. In DevEco Studio, create an ArkTS app project, edit the **entry > src > main > ets > entryability > EntryAbility.ets** file in the project, and import the dependent modules. The sample code is as follows:

   <!-- @[MainThreadJank_ArkTS_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
   // ...
   import { buffer, util } from '@kit.ArkTS';
   import { fileIo } from '@kit.CoreFileKit';
   ```

2. In the **entry/src/main/ets/entryability/EntryAbility.ets** file of the project, add a watcher in lifecycle APIs such as **onCreate()** and **onForeground()** at a proper position. The sample code is as follows:

   <!-- @[MainThreadJank_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
   
   ``` TypeScript
   // Add a watcher for main thread jank events.
   hiAppEvent.addWatcher({
     // You can customize the watcher name. The system uses the name to identify different watchers.
     name: "mainThreadWatcher",
     // Subscribe to the system events of interest. Here, main thread jank events are subscribed to.
     appEventFilters: [
       {
         domain: hiAppEvent.domain.OS,
         names: [hiAppEvent.event.MAIN_THREAD_JANK]
       }
     ],
     // Implement the real-time subscription callback to customize the processing of subscribed event data.
     onReceive: (domain: string, appEventGroups: Array<hiAppEvent.AppEventGroup>) => {
       hilog.info(0x0000, 'testTag', `HiAppEvent onReceive: domain=${domain}`);
       for (const eventGroup of appEventGroups) {
         // Use the event names in the event group to distinguish different system events.
         hilog.info(0x0000, 'testTag', `HiAppEvent eventName=${eventGroup.name}`);
         for (const eventInfo of eventGroup.appEventInfos) {
           // Customize the processing of event data in the event group. Here, the event data is printed in logs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.domain=${eventInfo.domain}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.name=${eventInfo.name}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.eventType=${eventInfo.eventType}`);
           // Obtain the timestamp of the main thread jank event.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.time=${eventInfo.params['time']}`);
           // Obtain the version of the application in which the main thread jank event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version=${eventInfo.params['bundle_version']}`);
           // Obtain the bundle name of the application in which the main thread jank event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_name=${eventInfo.params['bundle_name']}`);
           // Obtain the PID and UID of the application in which the main thread jank event occurs.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.pid=${eventInfo.params['pid']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.uid=${eventInfo.params['uid']}`);
           // Obtain the start and end times of main thread processing.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.begin_time=${eventInfo.params['begin_time']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.end_time=${eventInfo.params['end_time']}`);
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.log_over_limit=${eventInfo.params['log_over_limit']}`);
           // Obtain the task start time for the main thread jank event (a stack sampling parameter).
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.app_start_jiffies_time=${JSON.stringify(eventInfo.params['app_start_jiffies_time'])}`);
           // Obtain the most frequently printed call stack in the generated main thread jank log file (a stack sampling parameter).
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.heaviest_stack=${eventInfo.params['heaviest_stack']}`);
   
           // Obtain the fault log file for the main thread jank event.
           hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.external_log=${JSON.stringify(eventInfo.params['external_log'])}`);
           // Move the file to a new directory as follows.
           let path: string = String(eventInfo.params['external_log']);
           // Specify a custom storage path.
           let targetPath: string = "";
           if (path.endsWith(".txt")) {
             targetPath= "/data/storage/el2/base/mainThreadJank.txt";
           } else if (path.endsWith(".trace")) {
             targetPath= "/data/storage/el2/base/mainThreadJank.trace";
           }
           try {
             fileIo.copyFileSync(path.toString(), targetPath.toString());
           } catch (e) {
             hilog.error(0x0000, 'testTag', `copy file failed: ${e}`);
           }
         }
       }
     }
   });
   ```

3. Simulate a main thread timeout stack sampling event.

   Edit the **entry/src/main/ets/pages/Index.ets** file to add a button. In its **onClick** callback, simulate a main thread timeout to trigger a main thread jank event. The sample code is as follows:

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

4. (Optional) Simulate the customization of the main thread timeout parameter and trigger the main thread jank event.

   Edit the **entry > src > main > ets > pages> Index.ets** file in the project. In this example, a **customSample** button component is configured in **onClick()** to implement the custom sampling stack parameters. The sample code is as follows:

   Import the required module.
    <!-- @[MainThreadJankEvent_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->    
    
    ``` TypeScript
    import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
    ```

   Customize the stack sampling parameters.

    <!-- @[MainThreadJank_Set_Event_Config](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
    
    ``` TypeScript
    Button("customSample", { stateEffect:true, type: ButtonType.Capsule})
      .width('75%')
      .height(50)
      .margin(15)
      .fontSize(20)
      .fontWeight(FontWeight.Bold)
      .onClick(() => {
        // Write an event in the button click handler to record the button click.
        let params: Record<string, hiAppEvent.ParamType> = {
          // Log type: 0 (default), 1 (stack sampling only), or 2 (trace collection only).
          "log_type": "1",
          // Timeout duration and sampling interval.
          "sample_interval": "100",
          // Startup period during which detection is skipped.
          "ignore_startup_time": "11",
          // Number of samples.
          "sample_count": "21",
          // Number of event reports.
          "report_times_per_app": "3"
        };
        hiAppEvent.setEventConfig(hiAppEvent.event.MAIN_THREAD_JANK, params).then(() => {
          hilog.info(0x0000, 'testTag', `HiAppEvent success to set event params.`)
        }).catch((err: BusinessError) => {
          hilog.error(0x0000, 'testTag', `HiAppEvent err.code: ${err.code}, err.message: ${err.message}`)
        });
      })
    ```

   Trigger a 150 ms timeout event.

   <!-- @[MainThreadJank_Timeout_150_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Add a click handler to trigger MAIN_THREAD_JANK.
   Button('timeOut150')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       let t = Date.now();
       while (Date.now() - t <= 150) {}
     })
   ```

5. Simulate a main thread timeout trace sampling event.

   In the **entry/src/main/ets/pages/Index.ets** file of the project, add a button in **onClick()** to trigger the timeout trace capture. The sample code is as follows:

   > **NOTE**
   >
   > Before starting the timeout trace capture of the main thread, ensure that you use the [nolog version](performance-analysis-kit-terminology.md#nolog-version) and disable **Developer options**.

   <!-- @[MainThreadJank_Timeout_500_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
   
   ``` TypeScript
   // Add a click handler to trigger MAIN_THREAD_JANK.
   Button('timeOut500')
     .type(ButtonType.Capsule)
     .margin({
       top: 20
     })
     .backgroundColor('#0D9FFB')
     .width('80%')
     .height('5%')
     .onClick(() => {
       let t = Date.now();
       while (Date.now() - t <= 500) {}
     })
   ```

6. Click the **Run** button in DevEco Studio to run the project.

   > **NOTE**
   >
   > By default, the system starts main thread jank event detection 10 seconds after the application is launched because the application startup process is time-consuming.
   >
   > If you use the **setEventConfig** API to set sampling stack parameters, the system starts main thread jank event detection after the time specified by **ignore_startup_time**.

   The main thread jank event is triggered when two consecutive timeout events are detected within the interval of the detection task.
  
   You can quickly click the timeout button for two or three times (for example, **timeOut350**, **timeOut150**, or **timeOut500**) to trigger the main thread jank event.

### Verifying the Subscription

1. After the main thread jank event is reported, the system calls **onReceive()**. You can view the following event information in the **Log** window.

   Trace data of the main thread jank event is as follows:

   ```text
    HiAppEvent eventInfo.domain=OS
    HiAppEvent eventInfo.name=MAIN_THREAD_JANK
    HiAppEvent eventInfo.eventType=1
    HiAppEvent eventInfo.params.time=1717593620518
    HiAppEvent eventInfo.params.bundle_version=1.0.0
    HiAppEvent eventInfo.params.bundle_name=com.example.main_thread_jank
    HiAppEvent eventInfo.params.pid=40986
    HiAppEvent eventInfo.params.uid=20020150
    HiAppEvent eventInfo.params.begin_time=1717593620016
    HiAppEvent eventInfo.params.end_time=1717593620518
    HiAppEvent eventInfo.params.external_log=["/data/storage/el2/log/watchdog/MAIN_THREAD_JANK_20240613211739_40986.XXX"]
    HiAppEvent eventInfo.params.log_over_limit=false
    HiAppEvent eventInfo.params.app_start_jiffies_time=XXXX
    HiAppEvent eventInfo.params.heaviest_stack=XXXX
   ```

   The sampling stack of the main thread jank event is similar to the trace result. The differences are as follows:

   ```text
   Stack:
     The app_start_jiffies_time and heaviest_stack parameters are added to the sampling stack.
     external_log=["/data/storage/el2/log/watchdog/MAIN_THREAD_JANK_yyyyMMDDHHmmss_xxxx.txt"]. xxxx indicates the process ID.
   
   Trace:
     external_log=[""/data/storage/el2/log/watchdog/MAIN_THREAD_JANK_unix timestamp_xxxx.trace"]. xxxx indicates the process ID.
   ```
