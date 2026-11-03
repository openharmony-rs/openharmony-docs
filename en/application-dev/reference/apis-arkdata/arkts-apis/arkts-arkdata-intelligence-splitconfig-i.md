# SplitConfig

```TypeScript
interface SplitConfig
```

Represents the configuration for text splitting.

**Since:** 15

<!--Device-intelligence-interface SplitConfig--><!--Device-intelligence-interface SplitConfig-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## overlapRatio

```TypeScript
overlapRatio: number
```

Overlap ratio between adjacent chunks. The value ranges from 0 to 1, where **0** indicates the lowest overlap ratio and **1** indicates the highest overlap ratio. A higher overlap ratio is suitable for long-text scenarios that require semantic continuity, while a lower ratio is suitable for short-text scenarios that require reduced duplicate computation.

**Type:** number

**Since:** 15

<!--Device-SplitConfig-overlapRatio: double--><!--Device-SplitConfig-overlapRatio: double-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## size

```TypeScript
size: number
```

Maximum size of a chunk, which is a non-negative integer. A smaller size value is suitable for scenarios that require fine-grained chunking or have memory constraints, while a larger size value is suitable for reducing the number of chunks when processing large amounts of data.

**Type:** number

**Since:** 15

<!--Device-SplitConfig-size: int--><!--Device-SplitConfig-size: int-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core
