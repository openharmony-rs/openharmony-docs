# ParallelStrategy

```TypeScript
export enum ParallelStrategy
```

ParallelStrategy作为[Options](arkts-basicservices-zlib-options-i.md#Options)的一个属性，用于指定压缩或解压时的串行或并行策略。

**起始版本：** 18

**系统能力：** SystemCapability.BundleManager.Zlib

## PARALLEL_STRATEGY_SEQUENTIAL

```TypeScript
PARALLEL_STRATEGY_SEQUENTIAL = 0
```

默认值，串行压缩/解压策略。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

## PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION

```TypeScript
PARALLEL_STRATEGY_PARALLEL_DECOMPRESSION = 1
```

并行解压策略。

**起始版本：** 18

**原子化服务API：** 该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.BundleManager.Zlib

