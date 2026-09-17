# finishAsyncTrace

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## finishAsyncTrace

```TypeScript
function finishAsyncTrace(level: HiTraceOutputLevel, name: string, taskId: number): void
```

Stops an asynchronous trace with the trace output level specified.

The **level**, **name**, and **taskId** used in **finishAsyncTrace()** must be the same as those of [startAsyncTrace()](arkts-performanceanalysis-hitracemeter-startasynctrace-f.md).

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | Yes | Trace output level. |
| name | string | Yes | Name of the trace to start. |
| taskId | number | Yes | Task ID. |

**Examples**

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// Start trace tasks with the same name concurrently.
// Start the first trace.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// Service flow...
// Start the second trace with the same name while the first trace is still running. The tasks are running concurrently and therefore their taskId must be different.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 2, "categoryTest", "key=value");
// Service flow...
// Stop the first trace.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
// Service flow...
// Stop the second trace.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 2);
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// Start trace tasks with the same name in serial mode.
// Start the first trace.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// Service flow...
// Stop the first trace.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
// Service flow...
// Start the second trace with the same name. The traces with the same name are executed in serial mode.
hiTraceMeter.startAsyncTrace(COMMERCIAL, "myTestFunc", 1, "categoryTest", "key=value");
// Service flow...
// Stop the second trace with the same name.
hiTraceMeter.finishAsyncTrace(COMMERCIAL, "myTestFunc", 1);
```
