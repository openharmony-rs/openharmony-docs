# @ohos.bytrace (ByTrace)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @yu_haoqiaida-->
<!--Designer: @MontSaintMichel-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0e8943e8b8dd159f54837747c5c7d06207b95bd2 translatedAt=2026-09-16T11:12:23.035Z pushedAt=2026-09-20T09:01:52.273Z -->

This module provides the capability of tracing process traces for application performance analysis. Developers can use performance tracing to track the execution time of key code segments, locate performance bottlenecks, and optimize application performance. It applies to scenarios such as application startup duration analysis, service process performance monitoring, and frame rate analysis.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with the superscript to indicate their earliest API version.
> - The APIs of this module are deprecated since API version 8. You are advised to use the new APIs [@ohos.hiTraceMeter](js-apis-hitracemeter.md) instead.

## Modules to Import

```ts
import { bytrace } from '@kit.PerformanceAnalysisKit';
```

## bytrace.startTrace

startTrace(name: string, taskId: number, expectedTime?: number): void

Marks the start of a timeslice trace task.

> **NOTE**
>
> - If multiple tasks with the same **name** need to be traced, or the same task needs to be traced multiple times, and these tracing tasks are executed concurrently, the **taskId** of each **startTrace** call must be different. If the tracing tasks with the same **name** are executed serially, the **taskId** can be the same. An example is provided in the **bytrace.finishTrace** example below.
> - This API is supported since API version 7 and deprecated since API version 8. You are advised to use [startTrace](js-apis-hitracemeter.md#hitracemeterstarttrace) instead.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Name of a timeslice trace task.|
| taskId | number | Yes| ID of a timeslice trace task.|
| **expectedTime** | **number** | No | Expected duration (unit: ms). After this value is set, the system generates a performance warning when the actual execution time exceeds the expected value. Optional. The default value is empty, indicating that no warning is generated. |


**Example**

```ts
bytrace.startTrace("myTestFunc", 1);
bytrace.startTrace("myTestFunc", 1, 5); // The expected duration of the trace is 5 ms.
```

## bytrace.finishTrace

finishTrace(name: string, taskId: number): void

Marks the end of a timeslice trace task.

> **NOTE**
>
> - The **name** and **taskId** of **finishTrace** must be consistent with the corresponding parameter values of **startTrace** at the beginning of the process.
> - This API is supported since API version 7 and deprecated since API version 8. You are advised to use [finishTrace](js-apis-hitracemeter.md#hitracemeterfinishtrace) instead.

**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| **name** | **string** | Yes | Name of the time-slice tracing task, which must be consistent with the **name** parameter value in the **startTrace** call. |
| **taskId** | **number** | Yes | ID of the time-slice tracing task, which must be consistent with the **taskId** parameter value in the **startTrace** call. |

**Example**

```ts
bytrace.finishTrace("myTestFunc", 1);
```

```ts
// Start trace tasks with the same name concurrently.
bytrace.startTrace("myTestFunc", 1);
// Service flow...
bytrace.startTrace("myTestFunc", 2);  // The second trace task starts while the first task is still running. The first and second tasks have the same name but different task IDs.
// Service flow...
bytrace.finishTrace("myTestFunc", 1);
// Service flow...
bytrace.finishTrace("myTestFunc", 2);
```

```ts
// Start trace tasks with the same name in serial mode.
bytrace.startTrace("myTestFunc", 1);
// Service flow...
bytrace.finishTrace("myTestFunc", 1);  // The first trace task ends.
// Service flow...
bytrace.startTrace("myTestFunc", 1);   // The second trace task starts after the first task ends. The two tasks have the same name and task ID.
// Service flow...
bytrace.finishTrace("myTestFunc", 1);
```

## bytrace.traceByValue

traceByValue(name: string, count: number): void

Marks a numeric variable of a pre-tracing task whose value keeps changing. **traceByValue** can be used independently to record the change trace of a numeric variable.

> **NOTE**
>
> This API is supported since API version 7 and deprecated since API version 8. You are advised to use [traceByValue](js-apis-hitracemeter.md#hitracemetertracebyvalue) instead.


**System capability**: SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes| Name of the numeric variable.|
| **count** | **number** | Yes | Value of the numeric variable. |

**Example**

```ts
let traceCount = 3;
bytrace.traceByValue("myTestCount", traceCount);
traceCount = 4;
bytrace.traceByValue("myTestCount", traceCount);
// Service flow...
```
