# HiCollie_SetTimerParam

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @Chenyufan466765692-->
<!--Designer: @peterhuangyu-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=1d900df92d6661ea579d9ba078f8fe29054d3394 translatedAt=2026-09-16T10:27:41.805Z pushedAt=2026-09-20T09:01:52.234Z -->

```c
typedef struct HiCollie_SetTimerParam {...} HiCollie_SetTimerParam
```

## Overview

Defines the input parameters of the **OH_HiCollie_SetTimer** function, which are used to set the name of the timer monitoring task, the task timeout threshold, the timeout callback function, and the execution action flag.<br> Use case: applicable to scenarios where task execution time needs to be monitored, helping developers monitor and handle task timeout issues.

**Since**: 18

**Related module**: [HiCollie](capi-hicollie.md)

**Header file**: [hicollie.h](capi-hicollie-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char *name | Timer task name. The task name cannot be empty. |
| unsigned int timeout | Task timeout threshold, in seconds, which must be a positive integer greater than 0. When the task execution time exceeds this threshold, the timeout handling mechanism is triggered. Set it based on the actual service scenario. |
| [OH_HiCollie_Callback](capi-hicollie-h.md#oh_hicollie_callback) func | Callback executed when a timeout occurs.|
| void *arg | Parameters of the callback.|
| [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag) flag | Action performed when a timeout occurs. For details, see [HiCollie_Flag](capi-hicollie-h.md#hicollie_flag).|


