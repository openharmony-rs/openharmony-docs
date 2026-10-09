# Application Freeze Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=85aa562299b7054dce3d0e6b2f6a7c9f2482e25f translatedAt=2026-07-30T09:20:53.474Z pushedAt=2026-07-30T12:32:10.712Z -->

## Overview

AppFreeze (application freeze) means that an application does not respond to user operations (for example, clicking) for a specified period of time. To address application freeze problems, the system provides the application freeze detection, maintenance and debugging log capturing, and log reporting capabilities to help you locate faults.

This section introduces the detection principle of **AppFreeze** (app freeze) as well as the meaning and specifications of each field. To learn how to use HiAppEvent APIs to subscribe to app freeze events, refer to the following documents. Both ArkTS and C/C++ APIs are available; choose based on your needs.

- [Subscribing to Application Freeze Events (ArkTS)](hiappevent-watcher-freeze-events-arkts.md)

- [Subscribing to Application Freeze Events (C/C++)](hiappevent-watcher-freeze-events-ndk.md)

> **NOTE**
>
> App freeze events can be subscribed to using HiAppEvent in [application clones](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone) and atomic services. Since API version 22, app freeze events can be subscribed to using HiAppEvent in [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide).

## Detection Principles

For details, see [Application Freeze Detection Principles](appfreeze-guidelines.md#detection-principles).

## Custom Parameter Settings for Page Transition Log Specification

Supported since **API version 24**, page transition log configuration allows the system to collect and report page transition logs when an app freeze occurs, helping you locate issues.

### configEventPolicy

| API | Description |
| -------- | -------- |
| [configEventPolicy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventconfigeventpolicy22) (policy: EventPolicy): Promise&lt;void>| Sets the policy parameters for app freeze events. This API supports enabling page transition log collection for app freeze events. |

### configEventPolicy Parameter Settings

You can enable page transition log collection for app freeze events by setting parameters in [EventPolicy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#eventpolicy22).

| Name | Type | Read-only | Optional | Description |
| ---------- | ------- | ---- | ---- | ------------------------------------------ |
| appFreezePolicy | [AppFreezePolicy](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#appfreezepolicy24) | No | Yes | Configuration policy for app freeze events. |

**Parameter Setting Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog, hiAppEvent } from '@kit.PerformanceAnalysisKit';

let policy: hiAppEvent.EventPolicy = {
    "appFreezePolicy" : {
      "pageSwitchLogEnable": true // Enable page transition log.
    }
};
hiAppEvent.configEventPolicy(policy).then(() => {
    hilog.info(0x0000, 'hiAppEvent', `Set crash config policy successfully.`);
}).catch((err: BusinessError) => {
    hilog.error(0x0000, 'hiAppEvent', `Failed to set crash config policy. code: ${err.code}, message: ${err.message}`);
});
```

## Event Fields

### params

The **params** attribute in the event information is described as follows.

| Name| Type| Description|
| -------- | -------- | -------- |
| time | number | Event triggering time, in ms.|
| foreground | boolean | Whether the application is running in the foreground. The value **true** indicates that the application is in the foreground, and the value **false** indicates the opposite.|
| release_type | string | App version type. The value **release** indicates that the app is a [release-type app](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916), and the value **debug** indicates that the app is a [debug-type app](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/ide-hvigor-compilation-options-customizing-guide#section192461528194916).<br>**Note:** Supported since API version 23. |
| cpu_abi | string | ABI type.<br>Note: This field is supported since API version 23.|
| app_running_unique_id | string | Unique ID associated with the app runtime.<br>**Note:** This parameter is supported since API version 24. |
| bundle_version | string | Application version.|
| bundle_name | string | Application name.|
| process_name | string | Process name of the application.|
| pid | number | Process ID of an application.|
| uid | number | User ID of an application.|
| uuid | string | Error ID, which is generated based on fault information and uniquely identifies crash faults of the same type.|
| exception | object | Exception information. For details, see [exception](#exception). |
| hilog | string[] | Log information. For the application freeze event, a maximum of 100 lines of faulty process log information can be obtained from the hilog buffer.|
| event_handler | string[] | Events not yet handled by the main thread.|
| event_handler_size_3s | string | Number of tasks in the task stack at 3s in the [THREAD_BLOCK_6S event](appfreeze-guidelines.md#thread_block_6s-app-main-thread-freeze-timeout) (effective only for Application Not Responding events). |
| event_handler_size_6s | string | Number of tasks in the task stack at 6s in the [THREAD_BLOCK_6S event](appfreeze-guidelines.md#thread_block_6s-app-main-thread-freeze-timeout) (effective only for Application Not Responding events). |
| peer_binder | string[] | Binder call information.|
| threads | object[] | Full thread call stack. For details, see [thread](#thread). |
| memory | object | Memory information. For details, see [memory](#memory). |
| external_log<sup>12+</sup> | string[] | Path of the error log file. If the directory files exceed the threshold (for details, see **log_over_limit**), new log files may fail to be written. Therefore, delete the log files immediately after they are processed.|
| log_over_limit<sup>12+</sup> | boolean | Whether the total size of the generated fault log file and existing log files exceeds the 5 MB upper limit. The value **true** indicates that the upper limit is exceeded and log writing fails; **false** indicates that the upper limit is not exceeded.<br>When [minidump](performance-analysis-kit-terminology.md#minidump) is enabled, the upper limit is adjusted to 35 MB; when minidump is disabled, the upper limit is restored to 5 MB. |
| process_life_time | number | Fault process survival time.<br>**Note:** Supported since API version 22. |
| external_callback_log | string | Custom callback log information, which can be written through [OH_HiCollie_SetFreezeCallback](../reference/apis-performance-analysis-kit/capi-hicollie-h.md#oh_hicollie_setfreezecallback).<br>**Note:** Supported since API version 24. |
| page_switch_log | string | Page transition log path. For details about the log, see [Page Switch Logs](pageswitch-log.md).<br>**Note:** Supported since API version 24. |
| application_gc_info | object | App GC information. For details, see [application_gc_info](#application_gc_info).<br>**Note:** Supported since API version 26.0.0. |
| application_io_info | object | I/O information. For details, see [application_io_info](#application_io_info).<br>**Note:** Supported since API version 26.0.0. |

### exception

| Name| Type| Description|
| -------- | -------- | -------- |
| name | string | Exception type. |
| message | string | Exception cause. |

### thread

| Name| Type| Description|
| -------- | -------- | -------- |
| thread_name | string | Thread name.|
| tid | number | Thread ID.|
| frames | object[] | Thread call stack. For details, see [frame](#frame). |
| state | string | Thread running state, which is read from the value of **state** in **/proc/pid/stat**.<br>**Note:** This field is supported since API version 23.|
| utime | number | Number of CPU ticks consumed by the thread in user mode, which is read from the value of **utime** in **/proc/pid/stat**.<br>**Note:** This field is supported since API version 23.|
| stime | number | Number of CPU ticks consumed by the thread in kernel mode, which is read from the value of **stime** in **/proc/pid/stat**.<br>**Note:** This field is supported since API version 23.|
| priority | number | Real-time priority, which is read from the value of **priority** in **/proc/pid/stat**.<br>**Note:** This field is supported since API version 23.|
| nice | number | Static priority, which is read from the value of **nice** in **/proc/pid/stat**.<br>**Note:** This field is supported since API version 23.|
| clk | number | Number of clock ticks per second, which is obtained through **sysconf(_SC_CLK_TCK)**. If the value fails to be obtained, the default value **100** is used. The running time (unit: second) can be calculated by dividing the number of clock ticks by this value.<br>**Note:** This field is supported since API version 23.|

### frame

Native frame

| Name| Type| Description|
| -------- | -------- | -------- |
| symbol | string | Function name. If the name length exceeds 256 bytes, the name is deleted to prevent unknown issues.|
| file | string | File name.|
| buildId | string | Build ID from the **.note.gnu.build-id** section of the ELF file. |
| pc | string | Hexadecimal byte offset of the executed instruction within the file.|
| offset | number | Byte offset of the executed instruction within the function.|

For details, see [Call stack frame](cppcrash-guidelines.md#common-faults).

JS frame

| Name| Type| Description|
| -------- | -------- | -------- |
| file | string | File name. |
| packageName | string | Package name of the module. |
| symbol | string | Function name. |
| line | number | Line number of the code. |
| column | number | Column number of the code. |

For details, see [JS hybrid stack frame](cppcrash-guidelines.md#common-faults).

### memory

| Name| Type| Description|
| -------- | -------- | -------- |
| rss | number | Actual memory usage of the process, in KB. Corresponds to the Process Memory(kB) field in [Appfreeze logs](appfreeze-guidelines.md#header-information). |
| vss | number | Size of the virtual memory applied by a process from the system, in KB.|
| pss | number | Size of the physical memory actually used by a process, in KB.|
| sys_free_mem | number | Free memory size, in KB. Corresponds to the Free value of the Device Memory(kB) field in [Appfreeze logs](appfreeze-guidelines.md#header-information). |
| sys_avail_mem | number | Available memory size, in KB. Corresponds to the Available value of the Device Memory(kB) field in [Appfreeze logs](appfreeze-guidelines.md#header-information). |
| sys_total_mem | number | Total memory size, in KB. Corresponds to the Total value of the Device Memory(kB) field in [Appfreeze logs](appfreeze-guidelines.md#header-information). |
| vm_heap_total_size | number | Total heap memory size of the main virtual machine, in KB. Corresponds to the Total value of the MainHeap(bytes) field in [Appfreeze logs](appfreeze-guidelines.md#general-information-in-the-log-body).<br>Note: Supported since API version 22. |
| vm_heap_used_size | number | Size of surviving objects continuously tracked during the lifecycle of the main virtual machine, in KB. Corresponds to the Used value of the MainHeap(bytes) field in [Appfreeze logs](appfreeze-guidelines.md#general-information-in-the-log-body).<br>Note: Supported since API version 22. |
| vm_heap_shared_size | number | Size of surviving objects continuously tracked during the lifecycle of the main virtual machine, in KB. Corresponds to the Used value of the SharedHeap(bytes) field in [Appfreeze logs](appfreeze-guidelines.md#general-information-in-the-log-body).<br>Note: Supported since API version 26.0.0. |

### application_gc_info

| Name | Type | Description |
| -------- | -------- | -------- |
| count | number | Number of GC occurrences in the process. Unit: count.<br>**Note:** Supported since API version 26.0.0.|
| maxPause | number | Maximum GC pause duration in the process. Unit: ms.<br>**Note:** Supported since API version 26.0.0.|
| minPause | number | Minimum GC pause duration in the process. Unit: ms.<br>**Note:** Supported since API version 26.0.0.|
| averagePause | number | Average GC pause duration in the process. Unit: ms.<br>**Note:** Supported since API version 26.0.0.|
| lastStartTime | number | Start time of the last GC in the process. Unit: ms.<br>**Note:** Supported since API version 26.0.0.|
| lastEndTime | number | End time of the last GC in the process. Unit: ms.<br>**Note:** Supported since API version 26.0.0.|
| lastType | number | Type of the last GC in the process. GC types: [HPP YoungGC], [HPP OldGC], [CompressGC], [SharedGC].<br>**Note:** Supported since API version 26.0.0.|

### application_io_info

| Name | Type | Description |
| -------- | -------- | -------- |
| rchar | number | Total number of bytes read by the process from the storage layer, including cached reads. Unit: byte.<br>**Note:** Supported since API version 26.0.0.|
| wchar | number | Total number of bytes written by the process to the storage layer, including cached writes. Unit: byte.<br>**Note:** Supported since API version 26.0.0.|
| syscr | number | Number of physical read system calls initiated by the process, such as read, pread, and readv. Unit: count.<br>**Note:** Supported since API version 26.0.0.|
| syscw | number | Number of physical write system calls initiated by the process, such as write, pwrite, and writev. Unit: count.<br>**Note:** Supported since API version 26.0.0.|
| read_bytes | number | Number of bytes actually read by the process from the block device. Unit: byte. Corresponds to the actual disk read I/O volume.<br>**Note:** Supported since API version 26.0.0.|
| write_bytes | number | Number of bytes actually written by the process to the block device. Unit: byte. Corresponds to the actual disk write I/O volume.<br>**Note:** Supported since API version 26.0.0.|
| cancelled_write_bytes | number | Number of write bytes canceled due to truncation or overwriting. Unit: byte.<br>**Note:** Supported since API version 26.0.0.|

## Customizing Parameters for Application Freeze Events

### Available APIs

| Name| Description|
| -------- | -------- |
| setEventParam(params: Record&lt;string, ParamType>, domain: string, name?: string): Promise&lt;void> | Sets custom parameters for application freeze events.|

### Setting Parameters

You can use this API to subscribe to app freeze events with the name **hiAppEvent.event.APP_FREEZE**. For details, see [hiAppEvent.setEventParam](../reference/apis-performance-analysis-kit/js-apis-hiviewdfx-hiappevent.md#hiappeventseteventparam12).