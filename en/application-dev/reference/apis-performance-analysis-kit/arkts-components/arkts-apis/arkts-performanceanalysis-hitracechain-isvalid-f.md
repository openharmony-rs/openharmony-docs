# isValid

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## isValid

```TypeScript
function isValid(id: HiTraceId): boolean
```

Checks whether a **HiTraceId** instance is valid. This API returns the result synchronously.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | Yes | **HiTraceId** instance. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** indicates that **HiTraceId** is valid, and **false** indicates the opposite. |

**Examples**

```TypeScript
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// Set the value of traceIdIsvalid to true.
let traceIdIsvalid = hiTraceChain.isValid(traceId);
if (traceIdIsvalid) {
// Processing logic for the scenario where the validity check on the trace ID is successful.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```
