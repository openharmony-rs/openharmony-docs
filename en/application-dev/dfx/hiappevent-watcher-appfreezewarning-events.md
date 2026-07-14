# App Freeze Warning Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=abb2cbc3c0ee7701da88cfed86a07b11347a25be translatedAt=2026-07-08T06:43:56.091Z pushedAt=2026-07-08T10:00:49.948Z -->

## Overview

Starting from API version 26.0.0, during app runtime, if only warning events under [app freeze events](appfreeze-guidelines.md#detection-principles), such as **THREAD_BLOCK_3S** and **LIFECYCLE_HALF_TIMEOUT**, are triggered, the system classifies them as app freeze warning events. For such scenarios, the system provides capabilities including app freeze warning detection, diagnostic log capture, and log reporting, helping you identify risks early and pinpoint potential freeze or hang issues.

This section introduces the detection principle of **AppFreezeWarning** (app freeze warning) events as well as the meaning and specifications of each field. To learn how to use HiAppEvent APIs to subscribe to app freeze warning events, refer to the following documents. Both ArkTS and C/C++ APIs are available; choose based on your needs.

- [Subscribing to App Freeze Warning Events (ArkTS)](hiappevent-watcher-appfreezewarning-events-arkts.md)

- [Subscribing to App Freeze Warning Events (C/C++)](hiappevent-watcher-appfreezewarning-events-ndk.md)

> **NOTE**
>
> App freeze warning events can be subscribed to by using HiAppEvent in [app clone](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone), atomic service, and [input method app](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide) scenarios.

## Detection Principle

For details, see the description for **THREAD_BLOCK_3S** and **LIFECYCLE_HALF_TIMEOUT** warning events in [AppFreeze Detection Principles](appfreeze-guidelines.md#detection-principles).

## Event Field Description

### params

The following table describes the properties of the **params** field in an app freeze warning event.

| Name | Type | Description |
| -------- | -------- | -------- |
| time | number | Event trigger time, in milliseconds. |
| foreground | boolean | Whether the app is in the foreground. **true** indicates that the app is in the foreground; **false** indicates that the app is in the background. |
| bundle_version | string | App version. |
| bundle_version_code | number | App version code. |
| bundle_name | string | App name. |
| process_name | string | Process name of the app. |
| pid | number | Process ID of the app. |
| uid | number | User ID of the app. |
| exception | object | Exception information. For details, see [exception](#exception). |
| hilog | string[] | Log information. When an app unresponsiveness event log is generated, up to 1000 lines of faulty process log information are obtained from the hilog buffer. |
| event_handler | string[] | Unprocessed messages in the main thread. |
| peer_binder | string[] | Binder call information. |
| threads | object[] | Full thread call stack. For details, see [thread](#thread). |
| memory | object | Memory information. For details, see [memory](#memory). |
| process_life_time | number | Faulty process lifetime, in seconds. |
| app_running_unique_id | string | Unique ID associated with the app runtime. |

### exception

| Name | Type | Description |
| -------- | -------- | -------- |
| name | string | Exception type. |
| message | string | Exception cause. |

### thread

| Name | Type | Description |
| -------- | -------- | -------- |
| thread_name | string | Thread name. |
| tid | number | Thread ID. |
| frames | object[] | Thread call stack. For details, see [frames](#frames). |
| state | string | Thread running state. Read from the value of **state** in **/proc/pid/stat**. |
| utime | number | Number of CPU ticks consumed by the thread in user mode. Read from the value of **utime** in **/proc/pid/stat**. |
| stime | number | Number of CPU ticks consumed by the thread in kernel mode. Read from the value of **stime** in **/proc/pid/stat**. |
| priority | number | Real-time priority. Read from the value of **priority** in **/proc/pid/stat**. |
| nice | number | Static priority. Read from the value of **nice** in **/proc/pid/stat**. |
| clk | number | Number of clock ticks per second. Obtained using **sysconf(_SC_CLK_TCK)**. If the call fails, the default value **100** is used. Divide the number of clock ticks by this value to calculate the elapsed running time, in seconds. |

### frames

**Native stack frames**

| Name | Type | Description |
| -------- | -------- | -------- |
| symbol | string | Function name.<br/>**If the name exceeds 256 bytes, the excess part is truncated to prevent unknown issues caused by excessively long strings.** |
| file | string | File name. |
| buildId | string | Build ID from the **.note.gnu.build-id** section of the ELF file. |
| pc | string | Offset of the instruction executed by the program within the file, in hexadecimal bytes. |
| offset | number | Offset of the instruction executed by the program within the function, in bytes. |

For details, see [Common Faults](cppcrash-guidelines.md#common-faults).

**JavaScript stack frames**

| Name | Type | Description |
| -------- | -------- | -------- |
| file | string | File name. |
| packageName | string | Package name of the module. |
| symbol | string | Function name. |
| line | number | Line number of the code. |
| column | number | Column number of the code. |

For details, see [Common Faults](cppcrash-guidelines.md#common-faults).

### memory

| Name | Type | Description |
| -------- | -------- | -------- |
| rss | number | Actual memory size occupied by the process, in KB. |
| vss | number | Virtual memory size requested by the process from the system, in KB. |
| sys_free_mem | number | Free memory size, in KB. |
| sys_avail_mem | number | Available memory size, in KB. |
| sys_total_mem | number | Total memory size, in KB. |
| vm_heap_total_size | number | Total heap memory size of the main virtual machine, in KB. |
| vm_heap_used_size | number | Total size of live objects continuously tracked over the lifetime of the primary virtual machine, in KB. |