# GwpAsanOptions

GWP-ASan配置项。可用于配置是否使能、采样频率，以及最大分配的插槽数。

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## 导入模块

```TypeScript
```

## alwaysEnabled

```TypeScript
alwaysEnabled?: boolean
```

true：100%使能GWP-ASan。false：1/128概率使能GWP-ASan。默认值：false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## isRecover

```TypeScript
isRecover?: boolean
```

用于控制应用以100%概率开启GWP-ASan时，是否以可恢复模式运行。true：当GWP-ASan以100%概率开启时，应用以可恢复模式运行。在该模式下，系统检测到地址越界故障后，避免因检测机制本身导致进程崩溃；但对于已造成非法内存访问的错误，应用仍可能发生崩溃。false：当GWP-ASan以100%概率开启时，应用以不可恢复模式运行。默认值：false。注意：该参数只在“以100%概率开启GWP-ASan”场景下生效；1/128概率开启场景下默认为可恢复，不受isRecover控制。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## maxSimutaneousAllocations

```TypeScript
maxSimutaneousAllocations?: number
```

最大分配的插槽数，默认值为1000，需要传入大于0的正整数，若传入小数则向上取整。当插槽用尽时，新分配的内存将不再受监控。释放已使用的内存后，其占用的插槽将自动复用，以便于后续内存的监控。建议值：&lt;=20000，过大会可能导致VMA超限崩溃。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug

## sampleRate

```TypeScript
sampleRate?: number
```

GWP-ASan采样频率，默认值为2500，需要传入大于0的正整数，若传入小数则向上取整。1/sampleRate的概率对分配的内存进行采样。建议值：&gt;=1000，过小会显著影响性能。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.HiviewDFX.HiProfiler.HiDebug
