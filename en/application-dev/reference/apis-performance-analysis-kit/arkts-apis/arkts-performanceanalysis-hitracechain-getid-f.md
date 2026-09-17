# getId

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## getId

```TypeScript
function getId(): HiTraceId
```

Obtains the trace ID. This API returns the result synchronously.

Obtains the HiTrace ID in the TLS of the current thread.

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Return value:**

| Type | Description |
| --- | --- |
| [HiTraceId](arkts-performanceanalysis-hitracechain-hitraceid-i.md) | **HiTraceId** instance. |

**Examples**

```TypeScript
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// After the service logic is executed for several times, obtain the current trace ID.
let curTraceId = hiTraceChain.getId();
// The call chain IDs in the trace IDs obtained from the same call chain trace must be the same.
if (curTraceId.chainId != traceId.chainId) {
// Processing logic for exceptions.
}
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```
