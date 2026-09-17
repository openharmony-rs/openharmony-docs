# ModelConfig

Manages configurations of the embedding model.

@interface ModelConfig

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## cachePath

```TypeScript
cachePath?: string
```

If NPU is used for accelerating, a local path is required for model caching.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## isNpuAvailable

```TypeScript
isNpuAvailable: boolean
```

Indicates whether NPU is used.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## modelInfo

```TypeScript
modelInfo?: CloudModelInfo
```

Indicates cloud embedding model information.

**Type:** [CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## networkPolicy

```TypeScript
networkPolicy?: NetworkPolicy
```

Indicates cloud embedding model network policy.

**Type:** [NetworkPolicy](arkts-arkdata-intelligence-networkpolicy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## version

```TypeScript
version: ModelVersion
```

Version of the model. The outputs of text or image embedding models with the same version are in the same vector space.

**Type:** [ModelVersion](arkts-arkdata-intelligence-modelversion-e.md)

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core
