# SplitConfig

管理文本分块的配置信息。

@interface SplitConfig

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## overlapRatio

```TypeScript
overlapRatio: number
```

相邻分块之间的重叠比率。范围为[0,1]，0表示重叠比率最低，1表示重叠比率最高。较高的重叠比率适用于需要保持语义连贯性的长文本场景，较低的比率适用于需要减少重复计算的短文本场景。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## size

```TypeScript
size: number
```

分块的最大大小，取值为非负整数。较小的size值适用于需要精细化分块或处理内存受限场景，较大的size值适用于处理大数据量时减少分块数量。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core
