# HiTraceId

Defines a **HiTraceId** object.

**Since:** 8

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

**System capability:** SystemCapability.HiviewDFX.HiTrace

## flags

```TypeScript
flags?: number
```

Trace flag. The default value is **0**.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## parentSpanId

```TypeScript
parentSpanId?: number
```

Parent span ID. The default value is **0**.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace

## spanId

```TypeScript
spanId?: number
```

Span ID. The default value is **0**.

**Type:** number

**Since:** 8

**System capability:** SystemCapability.HiviewDFX.HiTrace
