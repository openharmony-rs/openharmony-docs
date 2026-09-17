# finishSyncTrace

## Modules to Import

```TypeScript
import { hiTraceMeter } from '@kit.PerformanceAnalysisKit';
```

## finishSyncTrace

```TypeScript
function finishSyncTrace(level: HiTraceOutputLevel): void
```

Stops a synchronous trace with the trace output level specified.

The **level** used in **finishSyncTrace** must be the same as that of [startSyncTrace()](arkts-performanceanalysis-hitracemeter-startsynctrace-f.md).

**Since:** 19

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| level | [HiTraceOutputLevel](arkts-performanceanalysis-hitracemeter-hitraceoutputlevel-e.md) | Yes | Trace output level. |

**Examples**

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
hiTraceMeter.finishSyncTrace(COMMERCIAL);
```

```TypeScript
const COMMERCIAL = hiTraceMeter.HiTraceOutputLevel.COMMERCIAL;
// The startSyncTrace and finishSyncTrace APIs can be nested and they matched each other based on proximity.
// Start the first trace.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc1", "key=value");
// Service flow...
// Start the second trace.
hiTraceMeter.startSyncTrace(COMMERCIAL, "myTestFunc2", "key=value");
// Service flow...
// Stop the second trace.
hiTraceMeter.finishSyncTrace(COMMERCIAL);
// Service flow...
// Stop the first trace.
hiTraceMeter.finishSyncTrace(COMMERCIAL);
```
