# clearId

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## clearId

```TypeScript
function clearId(): void
```

Clears the trace ID. This API returns the result synchronously.

Clears the HiTrace ID in the current thread's TLS.

**Since:** 8

<!--Device-hiTraceChain-function clearId(): void--><!--Device-hiTraceChain-function clearId(): void-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

**Examples**

```TypeScript
// Before the service starts, try to clear the trace ID.
hiTraceChain.clearId();
// Start tracing. The tracing flag is DEFAULT.
let traceId = hiTraceChain.begin("business", hiTraceChain.HiTraceFlag.DEFAULT);
// End the call chain trace after the service logic is executed for several times.
hiTraceChain.end(traceId);
```
