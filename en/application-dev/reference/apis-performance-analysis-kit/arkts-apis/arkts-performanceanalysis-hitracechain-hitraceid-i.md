# HiTraceId

```TypeScript
interface HiTraceId
```

Defines a **HiTraceId** object.

**Since:** 8

<!--Device-hiTraceChain-interface HiTraceId--><!--Device-hiTraceChain-interface HiTraceId-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

## Modules to Import

```TypeScript
import { hiTraceChain } from '@kit.PerformanceAnalysisKit';
```

## chainId

```TypeScript
chainId: bigint
```

Call chain ID.

**Type:** bigint

**Since:** 8

<!--Device-HiTraceId-chainId: bigint--><!--Device-HiTraceId-chainId: bigint-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

## flags

```TypeScript
flags?: number
```

Trace flag. The default value is **0**.

**Type:** number

**Since:** 8

<!--Device-HiTraceId-flags?: int--><!--Device-HiTraceId-flags?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

## parentSpanId

```TypeScript
parentSpanId?: number
```

Parent span ID. The default value is **0**.

**Type:** number

**Since:** 8

<!--Device-HiTraceId-parentSpanId?: int--><!--Device-HiTraceId-parentSpanId?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace

## spanId

```TypeScript
spanId?: number
```

Span ID. The default value is **0**.

**Type:** number

**Since:** 8

<!--Device-HiTraceId-spanId?: int--><!--Device-HiTraceId-spanId?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiTrace
