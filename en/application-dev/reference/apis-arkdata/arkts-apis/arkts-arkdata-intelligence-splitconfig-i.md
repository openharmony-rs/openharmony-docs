# SplitConfig

```TypeScript
interface SplitConfig
```

Manages text chunk process configurations.

@interface SplitConfig

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

The ratio of overlap between adjacent chunks.

**Type:** number

**Since:** 15

<!--Device-SplitConfig-overlapRatio: double--><!--Device-SplitConfig-overlapRatio: double-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## size

```TypeScript
size: number
```

The maximun size of chunks.

**Type:** number

**Since:** 15

<!--Device-SplitConfig-size: int--><!--Device-SplitConfig-size: int-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core
