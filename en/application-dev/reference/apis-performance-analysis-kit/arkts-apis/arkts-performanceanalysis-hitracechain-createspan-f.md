# createSpan

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## createSpan

```TypeScript
function createSpan(): HiTraceId
```

Creates a trace span. This API works in synchronous manner.

Specifically, create a **HiTraceId**, use the **chainId** and **spanId** in the TLS of the current thread to initialize the **chainId** and **parentSpanId** of the **HiTraceId**, generate a new **spanId** for the **HiTraceId**, and return the **HiTraceId**.

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
// Create a trace span after the service logic is executed for several times.
let spanTraceId = hiTraceChain.createSpan();
// The call chain IDs in the trace IDs obtained from the same call chain trace must be the same.
if (spanTraceId.chainId != traceId.chainId) {
// Processing logic for exceptions.
}
// Stop tracing after the service is complete.
hiTraceChain.end(traceId);
```
