# SplitConfig

管理文本分块的配置信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-intelligence-interface SplitConfig--><!--Device-intelligence-interface SplitConfig-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## overlapRatio

```TypeScript
overlapRatio: double
```

相邻分块之间的重叠比率。范围为[0,1]，0表示重叠比率最低，1表示重叠比率最高。较高的重叠比率适用于需要保持语义连贯性的长文本场景，较低的比率适用于需要减少重复计算的短文本场景。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SplitConfig-overlapRatio: double--><!--Device-SplitConfig-overlapRatio: double-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## size

```TypeScript
size: int
```

分块的最大大小，取值为非负整数。较小的size值适用于需要精细化分块或处理内存受限场景，较大的size值适用于处理大数据量时减少分块数量。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-SplitConfig-size: int--><!--Device-SplitConfig-size: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

