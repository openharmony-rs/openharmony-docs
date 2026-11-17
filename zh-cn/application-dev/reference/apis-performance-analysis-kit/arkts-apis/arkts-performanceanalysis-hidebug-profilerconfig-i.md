# ProfilerConfig

```TypeScript
interface ProfilerConfig
```

Profiler配置。

**起始版本：** 26.1.0

<!--Device-hidebug-interface ProfilerConfig--><!--Device-hidebug-interface ProfilerConfig-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## discardDestroyed

```TypeScript
discardDestroyed?: boolean
```

丢弃已释放的记录。取值约束：true或false。默认值：true。

**类型：** boolean

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-discardDestroyed?: boolean--><!--Device-ProfilerConfig-discardDestroyed?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## filterSize

```TypeScript
filterSize?: number
```

过滤器大小，单位为字节。取值应为[1,4294967295]内的整数。默认值：1024。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-filterSize?: int--><!--Device-ProfilerConfig-filterSize?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxAsyncNestingDepth

```TypeScript
maxAsyncNestingDepth?: number
```

最大异步嵌套深度。取值范围：[0,16]。默认值：1。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-maxAsyncNestingDepth?: int--><!--Device-ProfilerConfig-maxAsyncNestingDepth?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxAsyncTaskStackDepth

```TypeScript
maxAsyncTaskStackDepth?: number
```

异步任务最大栈深度。取值应为[1,256]内的整数。默认值：16。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-maxAsyncTaskStackDepth?: int--><!--Device-ProfilerConfig-maxAsyncTaskStackDepth?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxDurationSec

```TypeScript
maxDurationSec?: number
```

最大持续时间，单位为秒。取值应为[1,3600]内的整数。默认值：900。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-maxDurationSec?: int--><!--Device-ProfilerConfig-maxDurationSec?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxStackDepth

```TypeScript
maxStackDepth?: number
```

最大堆栈深度。取值范围：[1,30]。默认值：30。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-maxStackDepth?: int--><!--Device-ProfilerConfig-maxStackDepth?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sampleIntervalBytes

```TypeScript
sampleIntervalBytes?: number
```

采样间隔（以字节为单位）。取值范围：[384,4294967295]。默认值：384。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-sampleIntervalBytes?: int--><!--Device-ProfilerConfig-sampleIntervalBytes?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## statisticsIntervalSec

```TypeScript
statisticsIntervalSec?: number
```

统计时间间隔（秒）。取值应为[1,3600]内的整数。默认值：10。

**类型：** number

**起始版本：** 26.1.0

**模型约束：** 此接口可在Stage模型和FA模型下使用。

<!--Device-ProfilerConfig-statisticsIntervalSec?: int--><!--Device-ProfilerConfig-statisticsIntervalSec?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
