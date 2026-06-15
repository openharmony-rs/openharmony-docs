# Crash Event Overview
<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @chenshi51-->
<!--Designer: @Maplestory91-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->

## Overview

A crash is an unexpected exit of an application process. Specifically, crash events occur in the following scenarios:

1. **NativeCrash** events are generated when the native code does not process [crash signals](cppcrash-guidelines.md#crash-signals).

2. **JsError** events are generated when ArkTS/JS code does not process exceptions.

This topic describes the crash event detection principles, field meanings, and specifications. For details about how to use the ArkTs and C/C++ APIs provided by HiAppEvent to subscribe to system crash events, see the following documents: Currently, ArkTS and C/C++ APIs are provided. You can select the APIs as required.

- [Subscribing to Crash Events (ArkTS)](hiappevent-watcher-crash-events-arkts.md)

- [Subscribing to Crash Events (C/C++)](hiappevent-watcher-crash-events-ndk.md)

> **NOTE**
>
> Crash events can be subscribed to using HiAppEvent in [application clones](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone) and atomic services. Since API version 22, HiAppEvent can be used to subscribe to crash events in [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide)

## Detection Principles

### NativeCrash

Based on the POSIX signal mechanism, the process crash detection capability of the system is implemented as follows: When a process crashes, it receives a crash signal, enters the system signal registration handling process, collects crash information, generates an event, and reports the event to the crash event subscriber of the application process.

The system detects a process crash as follows:

1. After a process crashes, it receives a crash signal from the kernel, which is processed by the signal processing module registered by the process during startup.

2. After receiving the crash signal, the process saves the current process context and forks a child process to execute the ProcessDump command to capture crash information.

3. After collecting crash information, the ProcessDump process reports it to the HiView process. The HiView process stores the event information in the [application sandbox](../file-management/app-sandbox-directory.md).

4. The crash event watcher registered by HiAppEvent listens for the file changes in the application sandbox directory and delivers the event callback to the application process.

### JsError

In ArkTS, the JsError crash detection detects global exceptions, collects the error object types (such as **Error**, **TypeError**, and **ReferenceError**), and reports them to the HiView process. The HiView process stores the event information in the [application sandbox](../file-management/app-sandbox-directory.md). The crash event watcher registered by HiAppEvent listens for the file changes in the application sandbox directory and delivers the event callback to the application process, helping you quickly locate and rectify faults.

## Customizing Crash Log Specifications

Since API version 20, crash log specifications can be customized.

The system provides the common NativeCrash log generation feature and allows you to set crash log parameters to meet your requirements.

### setEventConfig

| Name| Description|
| -------- | -------- |
| setEventConfig(name: string, config: Record&lt;string, ParamType>): Promise&lt;void> | Sets crash log parameters. The **name** parameter must be set to the crash event name constant **hiappevent.event.APP_CRASH**. This API supports only **NativeCrash**.|

### Parameters of setEventConfig

You can set the crash log printing specifications in **Record&lt;string, ParamType>** by using the API provided by HiAppEvent. The specific parameter descriptions are as follows.

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| extend_pc_lr_printing | boolean | No| The value **true** means to print the memory values of the 248 bytes before and 256 bytes after the PC and LR in the 64-bit system, or print the memory values of the 124 bytes before and 128 bytes after the PC and LR in the 32-bit system.<br>The value **false** means to print the memory values of the 16 bytes before and 232 bytes after the PC and LR in the 64-bit system, or print the memory values of the 8 bytes before and 116 bytes after the PC and LR in the 32-bit system.<br>Default value: **false**.|
| log_file_cutoff_sz_bytes | number | No| The value range is (0, 5242880], in bytes.<br>The crash log is truncated to the specified size when this parameter is set.<br>Otherwise, the default value **0** is used, which means no truncation.|
| simplify_vma_printing | boolean | No| The value **true** means to print only the Virtual Memory Area (VMA) mapping information of the addresses in the crash log, that is, **Maps** in the crash log, to reduce the log size.<br>The value **false** means to print all VMA mapping information.<br>Default value: **false**.|

The following is an example of parameter settings:

```text
let configParams: Record<string, hiAppEvent.ParamType> = {
    "extend_pc_lr_printing": true, // Enable the functionality of printing the memory values near the PC and LR registers.
    "log_file_cutoff_sz_bytes": 102400, // Truncate the crash log to 100 KB.
    "simplify_vma_printing": true // Enable simplified printing of maps.
};
```

For example, on the 64-bit system, subscribe to crash events and set log configuration parameters by referring to [Subscribing to Crash Events (ArkTS)](hiappevent-watcher-crash-events-arkts.md#how-to-develop) and obtain the **NativeCrash** log content through the [external_log](#params) field. The following enabled configuration parameters are printed in the log:

```text
...
Build info:OpenHarmony 6.0.0.33
Enabled app log configs:    <- List of enabled configuration parameters. Only the configuration parameters that are not set to the default values are printed.
Extend pc lr printing:true  <- Set extend_pc_lr_printing to true.
Log cut off size:102400B    <- Truncate the crash log to 100 KB.
Simplify maps printing:true <- Set simplify_vma_printing to true.
Timestamp:2025-05-17 19:17:07.000
...
```

For details about the crash log, see [Application Crash Log Configured by HiAppEvent](cppcrash-guidelines.md#application-crash-log-configured-by-hiappevent).

### OH_HiAppEvent_SetEventConfig

Starting from API version 24, custom crash log specification settings and the application log concatenation function are supported.

| Name| Description|
| --- | --- |
| int [OH_HiAppEvent_SetEventConfig](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_seteventconfig)(const char* name, HiAppEvent_Config* config) | Implements custom crash log specification settings and application log concatenation. This API supports only **NativeCrash**.|

### Parameters of OH_HiAppEvent_SetEventConfig

| Name| Type| Mandatory| Description|
| --- | --- | --- | --- |
| name | const char* | Yes| Name of the application crash event. The value is the macro **EVENT_APP_CRASH**.|
| config | HiAppEvent_Config* | Yes| Configuration parameter for the application crash event. The configuration items of the config parameter can be set by using the [OH_HiAppEvent_SetConfigItem](../reference/apis-performance-analysis-kit/capi-hiappevent-h.md#oh_hiappevent_setconfigitem) function.|

| Item| Type| Mandatory| Description|
| --- | --- | --- | --- |
| Macro: OH_APP_CRASH_PARAM_EXTEND_PC_LR_PRINTING<br>String: extend_pc_lr_printing| const char* | No| Whether to print the memory content within the extended byte range of the PC and LR registers.<br>**"true"**: For 64-bit systems, prints memory values 248 bytes before and 256 bytes after the PC and LR register addresses. For 32-bit systems, prints memory values 124 bytes before and 128 bytes after the addresses.<br>**"false"**: For 64-bit systems, prints memory values 16 bytes before and 232 bytes after the PC and LR register addresses. For 32-bit systems, prints memory values 8 bytes before and 116 bytes after the addresses.<br>The default value is **"false"**.|
| Macro: OH_APP_CRASH_PARAM_LOG_FILE_CUTOFF_SZ_BYTES<br>String: log_file_cutoff_sz_bytes| const char* | No| Whether to truncate the **CPP_CRASH** log. The value range is (0, 5242880], in bytes.<br>The crash log is truncated to the specified size when this parameter is set.<br>Otherwise, the default value **0** is used, which means no truncation.|
| Macro: OH_APP_CRASH_PARAM_SIMPLIFY_VMA_PRINTING<br>String: simplify_vma_printing| const char* | No| Whether to print the Virtual Memory Area (VMA) mapping information of addresses in the crash log.<br>**"true"**: Prints only the VMA mapping information of addresses in the crash log (**Maps** in the crash log) to reduce the log size.<br>**"false"**: Prints all VMA mapping information.<br>The default value is **"false"**.|
| Macro: OH_APP_CRASH_PARAM_MERGE_CPPCRASH_APP_LOG<br>String: merge_cppcrash_app_log| const char* | No| Whether to concatenate logs from the application sandbox.<br>**"true"**: Concatenates application logs in Native Crash scenarios.<br>**"false"**: Does not concatenate application logs.<br>The application log path read by the framework is: *sandbox path* + *application bundle name* + **_CppCrash_AppMerge.log**, for example: **/data/storage/el2/log/com.samples.eventsub_CppCrash_AppMerge.log**.<br>If you choose to generate concatenated logs in the signal processing function, the maximum generation time must not exceed 5s. Logs cannot be concatenated if the time exceeds 5s.|

### Parameter Setting Example

Refer to [Subscribing to Crash Events (C/C++)](hiappevent-watcher-crash-events-ndk.md#how-to-develop) to subscribe to crash events and set log configuration parameters. Then, use the [external_log](#params) field to obtain the application log content concatenated with **NativeCrash**-type crashes

> **NOTE**
>
> The concatenated logs generated by the application must exist in the sandbox path.

## Custom Parameter Settings for Page Switch Log Specification

Supported from API version 24. When an application crashes, the system can collect and report page switch logs to help you locate issues.

### configEventPolicy

| Name| Description|
| -------- | -------- |
| [configEventPolicy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventconfigeventpolicy22) (policy: EventPolicy): Promise&lt;void>| Sets the crash event policy parameters. You can enable the collection of page switch logs for crash events.|

### Parameters of configEventPolicy

You can set the parameters of [EventPolicy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#eventpolicy22) to enable the collection of page switch logs for crash events.

| Name      | Type   | Read-Only| Optional| Description                                        |
| ---------- | ------- | ---- | ---- | ------------------------------------------ |
| appCrashPolicy | [AppCrashPolicy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#appcrashpolicy24) | No| Yes  | Crash event configuration policy.|

**Parameter Setting Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

let policy: hiAppEvent.EventPolicy = {
    "appCrashPolicy" : {
      "pageSwitchLogEnable": true // Enable page switch logs.
    }
};
hiAppEvent.configEventPolicy(policy).then(() => {
    hilog.info(0x0000, 'hiAppEvent', `Set crash config policy successfully.`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'hiAppEvent', `Failed to set crash config policy. code: ${err.code}, message: ${err.message}`);
});
```

## Fields

### params

**params** is the event parameter object in [AppEventInfo](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#appeventinfo), which consists of a parameter name and a parameter value.

The fields contained in **params** of a system event are defined by the event.

The following table lists the common information predefined in the crash event.

| Name| Type| Description|
| -------- | -------- | -------- |
| time | number | Event triggering time, in ms.|
| crash_type | string | Crash type, which can be **NativeCrash** (native exception) or **JsError** (JS exception). For details about the detection method, see [C++ Crash (Process Crash) Detection](cppcrash-guidelines.md) and [JS Crash (Process Crash) Detection](jscrash-guidelines.md).|
| foreground | boolean | Whether the application is running in the foreground. The value **true** indicates that the application is in the foreground, and the value **false** indicates the opposite.|
| release_type | string | Application version type. The value **release** indicates that the application is a [release-type application](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916), and the value **debug** indicates that the application is a [debug-type application](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916).<br>Note: This field is supported since API version 23.|
| cpu_abi | string | ABI type.<br>Note: This field is supported since API version 23.|
| app_running_unique_id | string | Unique ID associated with the application runtime.<br>**Note**: This parameter is supported since API version 24.|
| bundle_version | string | Application version.|
| bundle_name | string | Application name.|
| pid | number | Process ID of an application.|
| uid | number | User ID of an application.|
| uuid | string | Error ID, which is generated based on fault information and uniquely identifies crash faults of the same type.|
| exception | object | Exception information in brief. For details, see [exception](#exception). For details about all fault information, see the **external_log** file.|
| hilog | string[] | Log information, which displays a maximum of 100 lines of HiLog logs. For more logs, see the fault log file.|
| process_life_time | number | Lifetime of the faulty process, in seconds.<br>Note: This field is supported since API version 22.|
| memory | object | Memory information. For details, see [memory](#memory).<br>Note: This field is supported since API version 22.|
| threads | object[] | Full thread call stack. For details, see [thread](#thread). This field applies only to **NativeCrash** events.|
| external_log<sup></sup> | string[] | [Application sandbox path](../file-management/app-sandbox-directory.md) of the fault log file. You can read the fault log file through the path. To avoid failed writing of new log files due to insufficient directory space, delete the log files after they are processed. For details about the threshold, see the **log_over_limit** field.|
| log_over_limit | boolean | Whether the total size of the generated and existing fault log files exceeds the upper limit 5 MB. The value **true** indicates that the upper limit is exceeded and logs fail to be written. The value **false** indicates that the upper limit is not exceeded.|
| process_name | string | Name of the faulty process.<br>Note: This field is supported since API version 21.|
| page_switch_log | string | Path of page switch logs. For details, see [Page Switch Logs](pageswitch-log.md).<br>**Note**: This field is supported since API version 24.|

### exception

**exception** of **JsError**

| Name| Type| Description|
| -------- | -------- | -------- |
| name | string | Exception type.|
| message | string | Exception cause.|
| stack | string | Exception call stack.|
| thread_name | string | Thread name.<br>Note: This field is supported since API version 21.|

**exception** of **NativeCrash**

| Name| Type| Description|
| -------- | -------- | -------- |
| message | string | Exception cause.|
| signal | object | Signal information. For details, see [signal](#signal).|
| thread_name | string | Thread name.|
| tid | number | Thread ID.|
| frames | object[] | Thread call stack. For details, see [frame](#frame).|

### signal

For details, see [C++ Crash (Process Crash) Detection Implementation Principles](cppcrash-guidelines.md#implementation-principles).

| Name| Type| Description|
| -------- | -------- | -------- |
| signo | number | Signal value.|
| code | number | Level-2 signal category.|
| address | string | Address where an access error occurs.|

### thread

| Name| Type| Description|
| -------- | -------- | -------- |
| thread_name | string | Thread name.|
| tid | number | Thread ID.|
| frames | object[] | Thread call stack. For details, see [frame](#frame).|

### frame

Native **frame**

| Name| Type| Description|
| -------- | -------- | -------- |
| file | string | File name.|
| symbol | string | Function name. The symbol may be empty due to the following reasons:<br>1. The function name is not saved in the binary file.<br>2. The function name is deleted because it contains more than 256 bytes.|
| buildId | string | Unique file ID. The file may not contain **buildId**.|
| pc | string | Hexadecimal byte offset of the executed instruction within the file.|
| offset | number | Byte offset of the executed instruction within the function.|

For details, see [Call stack frame](cppcrash-guidelines.md#common-faults).

Js **frame**

| Name| Type| Description|
| -------- | -------- | -------- |
| file | string | File name.|
| packageName | string | Package name of the module.|
| symbol | string | Function name.|
| line | number | Code line number.|
| column | number | Code column number.|

For details, see [JS hybrid stack frame](cppcrash-guidelines.md#common-faults).

### memory

| Name| Type| Description|
| -------- | -------- | -------- |
| rss | number | Size of the memory allocated for a process, in KB. This field corresponds to the **Process Memory** field in [C++ crash logs](cppcrash-guidelines.md#log-specifications) or [JS crash logs](jscrash-guidelines.md#log-specifications).|
| sys_free_mem | number | Size of free memory, in KB. This field corresponds to **Free** of the **Device Memory** field in [C++ crash logs](cppcrash-guidelines.md#log-specifications) or [JS crash logs](jscrash-guidelines.md#log-specifications).|
| sys_avail_mem | number | Size of available memory, in KB. This field corresponds to **Available** of the **Device Memory** field in [C++ crash logs](cppcrash-guidelines.md#log-specifications) or [JS crash logs](jscrash-guidelines.md#log-specifications).|
| sys_total_mem | number | Total memory size, in KB. This field corresponds to **Total** of the **Device Memory** field in [C++ crash logs](cppcrash-guidelines.md#log-specifications) or [JS crash logs](jscrash-guidelines.md#log-specifications).|

## Customizing Crash Event Parameters

Currently, the crash event reports common system crash information, which may not meet your specific requirements. Therefore, the **setEventParam** method is provided to customize event reporting information.

### APIs

| Name| Description|
| -------- | -------- |
| setEventParam(params: Record&lt;string, ParamType>, domain: string, name?: string): Promise&lt;void> | Sets custom event parameters.|
