# GwpAsanOptions

GWP-ASan配置项。可用于配置是否使能、采样频率，以及最大分配的插槽数。

**起始版本：** 23

<!--Device-hidebug-interface GwpAsanOptions--><!--Device-hidebug-interface GwpAsanOptions-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
import { hidebug } from '@kit.PerformanceAnalysisKit';
```

## alwaysEnabled

```TypeScript
alwaysEnabled?: boolean
```

控制是否每次启动都使能GWP-ASan。true：100%使能GWP-ASan。false：1/128概率使能GWP-ASan。默认值：false。

**类型：** boolean

**起始版本：** 23

<!--Device-GwpAsanOptions-alwaysEnabled?: boolean--><!--Device-GwpAsanOptions-alwaysEnabled?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## isRecover

```TypeScript
isRecover?: boolean
```

用于控制应用以100%概率开启GWP-ASan时，是否以可恢复模式运行。true：当GWP-ASan以100%概率开启时，应用以可恢复模式运行。false：当GWP-ASan以100%概率开启时，应用以不可恢复模式运行。默认值：false。注意：该参数只在"以100%概率开启GWP-ASan"场景下生效；1/128概率开启场景下默认为可恢复，不受isRecover控制。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-GwpAsanOptions-isRecover?: boolean--><!--Device-GwpAsanOptions-isRecover?: boolean-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxSimutaneousAllocations

```TypeScript
maxSimutaneousAllocations?: int
```

最大分配的插槽数，默认值为1000，需要传入大于0的正整数，若传入小数则向上取整。当插槽用尽时，新分配的内存将不再受监控。释放已使用的内存后，其占用的插槽将自动复用。建议值：&lt;=20000，过大会可能导致VMA超限崩溃。

**类型：** int

**起始版本：** 23

<!--Device-GwpAsanOptions-maxSimutaneousAllocations?: int--><!--Device-GwpAsanOptions-maxSimutaneousAllocations?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sampleRate

```TypeScript
sampleRate?: int
```

GWP-ASan采样频率，默认值为2500，需要传入大于0的正整数，若传入小数则向上取整。1/sampleRate的概率对分配的内存进行采样。建议值：>=1000，过小会显著影响性能。

**类型：** int

**起始版本：** 23

<!--Device-GwpAsanOptions-sampleRate?: int--><!--Device-GwpAsanOptions-sampleRate?: int-End-->

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

