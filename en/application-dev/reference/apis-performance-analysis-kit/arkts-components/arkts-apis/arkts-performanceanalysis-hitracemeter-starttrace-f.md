# startTrace

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## startTrace

```TypeScript
function startTrace(name: string, taskId: number): void
```

Starts an asynchronous trace.

If multiple trace tasks with the same name need to be performed at the same time or a trace needs to be performed multiple times concurrently, different task IDs must be specified in **startTrace**.

If the trace tasks with the same name are not performed at the same time, the same taskId can be used. For a specific example, see [finishTrace()](arkts-performanceanalysis-hitracemeter-finishtrace-f.md).

Since API version 19, you are advised to use [startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md), which must be used together with [finishAsyncTrace()](arkts-performanceanalysis-hitracemeter-finishasynctrace-f.md). In this way, you can specify the trace output level and category.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the trace to start. The maximum length of a trace record is 512 bytes. The excess part will be truncated. It is recommended that the length of this parameter be less than or equal to 420 bytes. |
| taskId | number | Yes | Task ID. It is used to distinguish multiple tasks with the same name. Ensure that the task IDs of concurrently executed tasks with the same name are unique. |

**Examples**

```TypeScript
hiTraceMeter.startTrace("myTestFunc", 1);  // Start the asynchronous tracing task.
```
