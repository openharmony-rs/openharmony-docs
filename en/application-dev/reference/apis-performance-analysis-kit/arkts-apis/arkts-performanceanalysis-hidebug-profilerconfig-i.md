# ProfilerConfig

```TypeScript
interface ProfilerConfig
```

Profiler configuration.

**Since:** 26.1.0

<!--Device-hidebug-interface ProfilerConfig--><!--Device-hidebug-interface ProfilerConfig-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## Modules to Import

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## discardDestroyed

```TypeScript
discardDestroyed?: boolean
```

Discard destroyed records. Default value: true.

**Type:** boolean

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-discardDestroyed?: boolean--><!--Device-ProfilerConfig-discardDestroyed?: boolean-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## filterSize

```TypeScript
filterSize?: number
```

Filter size in bytes. Value range: [1,4294967295]. Default value: 1024.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-filterSize?: int--><!--Device-ProfilerConfig-filterSize?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxAsyncNestingDepth

```TypeScript
maxAsyncNestingDepth?: number
```

Maximum async nesting depth. Value range: [0,16]. Default value: 1.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-maxAsyncNestingDepth?: int--><!--Device-ProfilerConfig-maxAsyncNestingDepth?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxAsyncTaskStackDepth

```TypeScript
maxAsyncTaskStackDepth?: number
```

Maximum async task stack depth. The value must be an integer within [1,256]. Default value: 16.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-maxAsyncTaskStackDepth?: int--><!--Device-ProfilerConfig-maxAsyncTaskStackDepth?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxDurationSec

```TypeScript
maxDurationSec?: number
```

Maximum duration in second. The value must be an integer within [1,3600]. Default value: 900.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-maxDurationSec?: int--><!--Device-ProfilerConfig-maxDurationSec?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxStackDepth

```TypeScript
maxStackDepth?: number
```

Maximum stack depth. Value range: [1, 30]. Default value: 30.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-maxStackDepth?: int--><!--Device-ProfilerConfig-maxStackDepth?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sampleIntervalBytes

```TypeScript
sampleIntervalBytes?: number
```

Sample interval in bytes. Value range: [384,4294967295]. Default value: 384.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-sampleIntervalBytes?: int--><!--Device-ProfilerConfig-sampleIntervalBytes?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## statisticsIntervalSec

```TypeScript
statisticsIntervalSec?: number
```

Statistics interval in seconds. The value must be an integer within [1,3600]. Default value: 10.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ProfilerConfig-statisticsIntervalSec?: int--><!--Device-ProfilerConfig-statisticsIntervalSec?: int-End-->

**System capability:** SystemCapability.HiviewDFX.HiProfiler.HiDebug
