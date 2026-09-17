# enableFlag

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## enableFlag

```TypeScript
function enableFlag(id: HiTraceId, flag: HiTraceFlag): void
```

Enables the trace flag specified in HiTraceId. This API returns the result synchronously.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | Yes | **HiTraceId** instance for which the trace flag is enabled. |
| flag | [HiTraceFlag](arkts-performanceanalysis-hitracechain-hitraceflag-e.md) | Yes | Specified trace flag. |

**Examples**

```TypeScript
// Start tracing. The tracing flag is INCLUDE_ASYNC.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// Set the value of enabledDoNotCreateSpanFlag to false.
let enabledDoNotCreateSpanFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Set the DONOT_CREATE_SPAN trace flag.
hiTraceChain.enableFlag(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
// Set the value of enabledDoNotCreateSpanFlag to true.
enabledDoNotCreateSpanFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.DONOT_CREATE_SPAN);
if (enabledDoNotCreateSpanFlag) {
// Processing logic for the scenario where the DONOT_CREATE_SPAN trace flag has been set.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```
