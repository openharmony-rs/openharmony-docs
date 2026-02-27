# Subscribing to Crash Events (ArkTS)
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @chenshi51-->
<!--Designer: @Maplestory91-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @foryourself-->

## Overview

The following describes how to subscribe to application crash events by using the ArkTS APIs provided by HiAppEvent. For details about how to use the APIs (such as parameter restrictions and value ranges), see [@ohos.hiviewdfx.hiAppEvent (Application Event Logging)](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md).

> **NOTE**
>
> The ArkTS APIs can be used to subscribe to the **JsError** and **NativeCrash** events.

## Available APIs

| API| Description|
| -------- | -------- |
| addWatcher(watcher: Watcher): AppEventPackageHolder | Adds a watcher to listen for application events.|
| removeWatcher(watcher: Watcher): void | Removes a watcher to unsubscribe from application events.|

## How to Develop

### Adding an Event Watcher

To subscribe to the crash event successfully, you are advised to add an event watcher after the application starts and before the service logic is executed.

The following describes how to subscribe to the crash event triggered by a button click.

1. Create a native C++ project in DevEco Studio. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, import the dependent modules. The sample code is as follows:

    <!-- @[Crash_Click_ArkTS_Header](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    import { hiAppEvent, hilog } from '@kit.PerformanceAnalysisKit';
    import { deviceInfo } from '@kit.BasicServicesKit';
    ```

2. In the **entry/src/main/ets/entryability/EntryAbility.ets** file, set the [custom parameters of the crash event](hiappevent-watcher-crash-events.md#customizing-crash-event-parameters) and [custom parameters of the crash log specifications](hiappevent-watcher-crash-events.md#customizing-crash-log-specifications) in **onCreate()**.


    <!-- @[Crash_ArkTS_Add_Event](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    // Build custom parameters for the crash event.
    let crashParams: Record<string, hiAppEvent.ParamType> = {
      "test_data": 100, // test_data is the custom data. You can customize the params parameter as required.
    };
    // Set custom parameters for the crash event.
    hiAppEvent.setEventParam(crashParams, hiAppEvent.domain.OS, hiAppEvent.event.APP_CRASH).then(() => {
      hilog.info(0x0000, 'testTag', `HiAppEvent success to set event param`);
    }).catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', `HiAppEvent code: ${err.code}, message: ${err.message}`);
    });
    
    if (deviceInfo.sdkApiVersion >= 20) {  // Since API Version 20, you can set crash log configuration parameters.
      // Build custom parameters for crash log specifications.
      let crashConfigParams: Record<string, hiAppEvent.ParamType> = {
        "extend_pc_lr_printing": true, // Enable the functionality of printing the memory values near the PC and LR.
        "log_file_cutoff_sz_bytes": 1024000, // Truncate the crash log to 1000 KB.
        "simplify_vma_printing": true // Enable simplified printing of maps.
      };
      // Set the crash log configuration parameters.
      hiAppEvent.setEventConfig(hiAppEvent.event.APP_CRASH, crashConfigParams).then(() => {
        hilog.info(0x0000, 'testTag', `HiAppEvent success to set event config.`);
      }).catch((err: BusinessError) => {
        hilog.error(0x0000, 'testTag', `HiAppEvent code: ${err.code}, message: ${err.message}`);
      });
    }
    ```

3. In the **entry/src/main/ets/entryability/EntryAbility.ets** file of the project, add a watcher in **onCreate()** to subscribe to system events. The sample code is as follows:

    <!-- @[CrashEvent_ArkTS_Add_Watcher](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/entryability/EntryAbility.ets) -->
    
    ``` TypeScript
    // Add a crash event watcher.
    let watcher: hiAppEvent.Watcher = {
      // Set the watcher name. The system identifies different watchers based on their names.
      name: 'crashEventWatcher',
      // Add the system events to watch, for example, crash events.
      appEventFilters: [
        {
          domain: hiAppEvent.domain.OS,
          names: [hiAppEvent.event.APP_CRASH]
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
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.eventType=${eventInfo.eventType}`);
            // Obtain the timestamp of the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.time=${eventInfo.params['time']}`);
            // Obtain the type of the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.crash_type=${eventInfo.params['crash_type']}`);
            // Obtain the foreground and background status of the crashed application.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.foreground=${eventInfo.params['foreground']}`);
            // Obtain the version information of the crashed application.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_version=${eventInfo.params['bundle_version']}`);
            // Obtain the bundle name of the crashed application.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.bundle_name=${eventInfo.params['bundle_name']}`);
            // Obtain the process ID of the crashed application.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.pid=${eventInfo.params['pid']}`);
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.uid=${eventInfo.params['uid']}`);
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.uuid=${eventInfo.params['uuid']}`);
            // Obtain the exception type, cause, and call stack of the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.exception=${JSON.stringify(eventInfo.params['exception'])}`);
            // Obtain the log information about the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.hilog.size=${eventInfo.params['hilog'].length}`);
            // Obtain the lifetime of the faulty process when the crash event occurs.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.process_life_time=${eventInfo.params['process_life_time']}`);
            // Obtain the memory information about the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.memory=${JSON.stringify(eventInfo.params['memory'])}`);
            // Obtain the crash log file about the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.external_log=${JSON.stringify(eventInfo.params['external_log'])}`);
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.log_over_limit=${eventInfo.params['log_over_limit']}`);
            // Obtain the custom test_data of the crash event.
            hilog.info(0x0000, 'testTag', `HiAppEvent eventInfo.params.test_data=${eventInfo.params['test_data']}`);
          }
        }
      }
    };
    hiAppEvent.addWatcher(watcher);
    ```

4. Construct a crash scenario.

    - Construct a **NativeCrash**

      In **entry/src/main/cpp/napi_init.cpp** of the project, add the **TestNullptr** method, and register it as an ArkTS API as follows:

      <!-- @[Sys_Native_Nullptr_Event_C++](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
      
      ``` C++
      static napi_value TestNullptr(napi_env env, napi_callback_info info)
      {
          int *p = nullptr;
          int a = *p; // Null pointer dereference. The program crashes.
          return {};
      }
      ```

      <!-- @[Sys_Native_Nullptr_Event_C++_Init](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/napi_init.cpp) -->
      
      ``` C++
      static napi_value Init(napi_env env, napi_value exports)
      {
          napi_property_descriptor desc[] = {
              // ···
              { "testNullptr", nullptr, TestNullptr, nullptr, nullptr, nullptr, napi_default, nullptr },
              // ···
          };
          napi_define_properties(env, exports, sizeof(desc) / sizeof(desc[0]), desc);
          return exports;
      }
      ```

      Define the ArkTS API in the **index.d.ts** file.

      <!-- @[Sys_Native_Crash_Event_C++_Index.d.ts](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/cpp/types/libentry/Index.d.ts) -->
      
      ``` TypeScript
      export const testNullptr: () => void;
      ```

      In the **entry/src/main/ets/pages/index.ets** file, add the **appCrash** button and construct a scenario for triggering a crash event in **onClick()**. The sample code is as follows:

      <!-- @[Native_CrashEvent_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
      
      ``` TypeScript
      Button('NativeCrash')
        .type(ButtonType.Capsule)
        .margin({
          top: 20
        })
        .backgroundColor('#0D9FFB')
        .width('80%')
        .height('5%')
        .onClick(() => {
          // Construct a scenario in onClick() to trigger a crash event.
          testNapi.testNullptr();
        })
      ```

    - Construct a **JsError**

      In the **entry/src/main/ets/pages/index.ets** file, add the **appCrash** button and construct a scenario for triggering a crash event in **onClick()**. The sample code is as follows:

      <!-- @[JsError_CrashEvent_Button](https://gitcode.com/openharmony/applications_app_samples/blob/master/code/DocsSample/PerformanceAnalysisKit/HiAppEvent/EventSub/entry/src/main/ets/pages/Index.ets) -->
      
      ``` TypeScript
      Button('JsError')
        .type(ButtonType.Capsule)
        .margin({
          top: 20
        })
        .backgroundColor('#0D9FFB')
        .width('80%')
        .height('5%')
        .onClick(() => {
          // Construct a scenario in onClick() to trigger a crash event.
          JSON.parse('');
        })
      ```

5. In DevEco Studio, click the **Run** button to run the project. Tap the **NativeCrash** or **JsError** button on the application screen to trigger a crash event. The system generates logs based on the crash type and triggers the callback.

> **NOTE**
>
> **JsError** collects fault information in process and triggers the callback almost instantly. **NativeCrash** collects it out of process, taking roughly 2s on average; the exact time depends on the number of service threads and IPC overhead. The collected fault information is reported asynchronously, which does not block the current service.

### Checking Whether a Watcher Subscribes to Crash Events

Depending on whether an application proactively captures crash events, callbacks are triggered for the crash events at different times. You need to check whether crash events are subscribed to at different times.

**Application not proactively captures crash events**

If the application does not proactively capture the crash exception, the application will exit after the system handles the crash. When the application restarts, HiAppEvent reports the crash event to the registered watcher to complete the callback.

If the application fails to start or remains unstarted for a long time, you can delay the event notification by referring to [Using FaultLogExtensionAbility to Subscribe to Events](./fault-log-extension-app-events-arkts.md).

**Application proactively captures crash events**

If an application proactively captures the crash event, a callback is triggered before the application exits. The following are examples:

1. The application does not exit during exception handling.

   When [errorManager.on](../reference/apis-ability-kit/js-apis-app-ability-errorManager.md#errormanageronerror) is used to capture the **JsError** crash event, a callback is triggered before the application exits. If the application registers the [crash signal](cppcrash-guidelines.md#crash-signals) processing function but does not exit, the **NativeCrash** event triggers a callback before the application exits.

2. If the exception handling takes a long time, the application exits with a delay.

In the development and debugging phase, after HiAppEvent reports a crash event and completes the callback, you can view the **JsError** event information in the **HiLog** window of DevEco Studio. The content of the **NativeCrash** event is different. For details, see [Event Fields](hiappevent-watcher-crash-events.md#fields). The following is an example of a **JsError** event:

```text
HiAppEvent onReceive: domain=OS
HiAppEvent eventName=APP_CRASH
HiAppEvent eventInfo.domain=OS
HiAppEvent eventInfo.name=APP_CRASH
HiAppEvent eventInfo.eventType=1
HiAppEvent eventInfo.params.time=1503045716054
HiAppEvent eventInfo.params.crash_type=JsError
HiAppEvent eventInfo.params.foreground=true
HiAppEvent eventInfo.params.bundle_version=1.0.0
HiAppEvent eventInfo.params.bundle_name=com.samples.eventsub
HiAppEvent eventInfo.params.pid=2610
HiAppEvent eventInfo.params.uid=20010044
HiAppEvent eventInfo.params.uuid=7c3b1579c8ca8629af3858f8145254c2867ee402dc16ee18034337aae258620b
HiAppEvent eventInfo.params.exception={"message":"Unexpected Text in JSON: Empty Text","name":"SyntaxError","stack":"    at anonymous (entry|entry|1.0.0|src/main/ets/pages/Index.ts:163:22)\n","thread_name":"amples.eventsub"}
HiAppEvent eventInfo.params.hilog.size=100
HiAppEvent eventInfo.params.process_life_time=25
HiAppEvent eventInfo.params.memory={"rss":181964,"sys_avail_mem":1230456,"sys_free_mem":676940,"sys_total_mem":2001932}
HiAppEvent eventInfo.params.external_log=["/data/storage/el2/log/hiappevent/APP_CRASH_1503045716408_2610.log"]
HiAppEvent eventInfo.params.log_over_limit=false
HiAppEvent eventInfo.params.test_data=100
```

## Migrating Crash Events from the FaultLogger API

The [@ohos.faultLogger (FaultLogger)](../reference/apis-performance-analysis-kit/js-apis-faultLogger.md) API is deprecated and no longer maintained since API version 18. You are advised to use the [@ohos.hiviewdfx.hiAppEvent](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md) API to subscribe to crash events. The following describes how to migrate the crash event subscription from the FaultLogger API to the HiAppEvent API.

**CPP_CRASH** and **JS_CRASH** defined in the [FaultType](../reference/apis-performance-analysis-kit/js-apis-faultLogger.md#faulttype) of FaultLogger are crash events.

Through HiAppEvent, you can subscribe to crash events by setting the event name to **hiAppEvent.event.APP_CRASH** and event domain to **hiAppEvent.domain.OS** in the **hiAppEvent.addWatcher** API.

You can identify the specific crash event by the **crash_type** field in [hiAppEvent.AppEventInfo.params](./hiappevent-watcher-crash-events.md#params).

The following table shows the mapping between the crash events.
| Faultlogger.FaultType | hiAppEvent.AppEventInfo.params.crash_type |
| --- | --- |
| CPP_CRASH | NativeCrash |
| JS_CRASH | JsError |

The following table shows the mapping between [FaultLogInfo](../reference/apis-performance-analysis-kit/js-apis-faultLogger.md#faultloginfo) and [hiAppEvent.AppEventInfo.params](./hiappevent-watcher-crash-events.md#params).
| Faultlogger.FaultLogInfo | hiAppEvent.AppEventInfo.params | Description|
| --- | --- | --- |
| pid | pid | None|
| uid | uid | None|
| type | crash_type | The event types are different. In FaultLogger, **type** is a fault type enumeration. In HiAppEvent, **crash_type** is a string.|
| timestamp | time | None|
| module | bundle_name | None|
| fullLog | external_log | **fullLog** indicates the fault log content. **external_log** indicates the application sandbox path of the fault log file. You can access the file to obtain the fault log content.|
| reason | **Reason** field in the **external_log** file| None|
| summary | Part of the** external_log** file| The **summary** of **CPP_CRASH** corresponds to the **Fault thread info** field in the **external_log** file. The **summary** of **JS_CRASH** corresponds to the **Error name**, **Error message**, **Stacktrace**, and **HybridStack** fields in the **external_log** file.|

Both [FaultLogger.query (using callback)](../reference/apis-performance-analysis-kit/js-apis-faultLogger.md#faultloggerquery9) and [FaultLogger.query (using promise)](../reference/apis-performance-analysis-kit/js-apis-faultLogger.md#faultloggerquery9-1) can use [hiAppEvent.addWatcher](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventaddwatcher) to implement the same functionality.

For details about how to use HiAppEvent to subscribe to crash events (ArkTS), see [How to Develop](#how-to-develop) and [Checking Whether a Watcher Subscribes to Crash Events](#checking-whether-a-watcher-subscribes-to-crash-events).
<!--RP1-->
<!--RP1End-->
