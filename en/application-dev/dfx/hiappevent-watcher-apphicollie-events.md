# Task Execution Timeout Event Overview

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=85aa562299b7054dce3d0e6b2f6a7c9f2482e25f translatedAt=2026-10-31T06:41:24.028Z pushedAt=2026-10-31T06:41:24.028Z nl=1 -->

## Overview

A task execution timeout occurs when monitored service code takes longer to execute than expected. To locate and analyze the problem, use [Task Execution Timeout Detection](apptask-timeout-guidelines.md#task-execution-timeout-detection) and analyze task execution based on the generated [log specifications](apptask-timeout-guidelines.md#log-specifications).

This topic describes task execution timeout detection principles and the meanings and specifications of event fields. To subscribe to task execution timeout events through HiAppEvent, see the following documents. Both ArkTS and C/C++ APIs are available.

- [Subscribing to Task Execution Timeout Events (ArkTS)](hiappevent-watcher-apphicollie-events-arkts.md).

- [Subscribing to Task Execution Timeout Events (C/C++)](hiappevent-watcher-apphicollie-events-ndk.md).

> **NOTE**
>
> You can subscribe to task execution timeout events through HiAppEvent in [app clone](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/app-clone) scenarios, but not in atomic service scenarios. Starting from API version 22, subscription is supported for [input method applications](https://developer.huawei.com/consumer/en/doc/harmonyos-guides/inputmethod-application-guide).

## Detection Principles

For details, see [Task Execution Timeout Detection Principles](apptask-timeout-guidelines.md#task-execution-timeout-detection).

## Event Fields

### params

The **params** attribute in a task execution timeout event contains the following fields:

| Name | Type | Description |
| -------- | -------- | -------- |
| time | number | Time when the event is triggered, in ms. |
| foreground | boolean | Whether the application is in the foreground. **true** means foreground; **false** means background. |
| bundle_version | string | Application version. |
| process_name | string | Application process name. |
| pid | number | Application process ID. |
| uid | number | Application user ID. |
| uuid | string | Fault fingerprint generated from fault information to identify crashes with the same characteristics. |
| exception | object | Exception information. For details, see [exception](#exception). |
| hilog | string[] | Log information. |
| peer_binder | string[] | Binder call information, including the call chain and related stack traces. |
| memory | object | Memory information. For details, see [memory](#memory). |
| external_log | string[] | Fault log file paths. **Delete log files promptly after processing them to prevent the directory from exceeding its capacity limit (see log_over_limit), which would cause new log files to fail to be written.** |
| log_over_limit | boolean | Whether the total size of newly generated and existing fault logs exceeds 5 MB. **true** means the limit is exceeded and log writing fails; **false** means it is not exceeded.<br>When [minidump](performance-analysis-kit-terminology.md#minidump) is enabled, the limit increases to 35 MB. When minidump is disabled, the limit returns to 5 MB. |
| external_callback_log | string | Custom callback log information, which can be written through [OH_HiCollie_SetFreezeCallback](../reference/apis-performance-analysis-kit/capi-hicollie-h.md#oh_hicollie_setfreezecallback).<br>**Note:** Supported starting from API version 24. |

### exception

The **exception** attribute contains the following fields:

| Name | Type | Description |
| -------- | -------- | -------- |
| name | string | Exception type. |
| message | string | Exception cause. |

### memory

The **memory** attribute contains the following fields:

| Name | Type | Description |
| -------- | -------- | -------- |
| rss | number | Resident memory occupied by the process, in KB. |
| vss | number | Virtual memory requested by the process, in KB. |
| pss | number | Physical memory actually used by the process, in KB. |
| sys_free_mem | number | Free memory, in KB. |
| sys_avail_mem | number | Available memory, in KB. |
| sys_total_mem | number | Total memory, in KB. |
