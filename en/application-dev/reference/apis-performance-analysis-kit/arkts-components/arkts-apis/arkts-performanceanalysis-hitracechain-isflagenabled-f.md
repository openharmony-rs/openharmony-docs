# isFlagEnabled

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## isFlagEnabled

```TypeScript
function isFlagEnabled(id: HiTraceId, flag: HiTraceFlag): boolean
```

Checks whether the trace flag is enabled for **HiTraceId**. This API returns the result synchronously.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | Yes | **HiTraceId** instance to be checked. |
| flag | [HiTraceFlag](arkts-performanceanalysis-hitracechain-hitraceflag-e.md) | Yes | Specified trace flag. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that the flag for **HiTraceId** is enabled, and **false** indicates the opposite. |

**Examples**

```TypeScript
// Start tracing. The tracing flag is INCLUDE_ASYNC.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
// Set the value of enabledIncludeAsyncFlag to true.
let enabledIncludeAsyncFlag = hiTraceChain.isFlagEnabled(traceId, hiTraceChain.HiTraceFlag.INCLUDE_ASYNC);
if (enabledIncludeAsyncFlag) {
// Processing logic for the scenario where the INCLUDE_ASYNC trace flag has been set.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```
