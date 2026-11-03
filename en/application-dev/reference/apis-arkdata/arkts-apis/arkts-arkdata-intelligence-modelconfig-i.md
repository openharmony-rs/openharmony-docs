# ModelConfig

```TypeScript
interface ModelConfig
```

Represents the configuration an embedded model.

**Since:** 15

<!--Device-intelligence-interface ModelConfig--><!--Device-intelligence-interface ModelConfig-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## cachePath

```TypeScript
cachePath?: string
```

If NPU is used for acceleration, a local path is required for model caching. The format is /xxx/xxx/xxx, where xxx is the path address, for example, "/data". The maximum length is 512 characters. The default value is "". An exception is thrown when the length exceeds the limit.

**Type:** string

**Since:** 15

<!--Device-ModelConfig-cachePath?: string--><!--Device-ModelConfig-cachePath?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## isNpuAvailable

```TypeScript
isNpuAvailable: boolean
```

Whether to use the NPU to accelerate the vectorization process. The value **true** means to use the NPU, and the value **false** means the opposite. If this parameter is set to **true** but the device does not support NPUs, loading an embedding model will trigger error 31300000.

**Type:** boolean

**Since:** 15

<!--Device-ModelConfig-isNpuAvailable: boolean--><!--Device-ModelConfig-isNpuAvailable: boolean-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## modelInfo

```TypeScript
modelInfo?: CloudModelInfo
```

Type and version information of the cloud-side model. Configure this parameter when a text embedding model is used. The supported model information is obtained through the [getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md) API. The default value is empty.

**Type:** [CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModelConfig-modelInfo?: CloudModelInfo--><!--Device-ModelConfig-modelInfo?: CloudModelInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## networkPolicy

```TypeScript
networkPolicy?: NetworkPolicy
```

Network policy used when downloading the cloud-side model. The default value is WIFI_ONLY. This parameter takes effect only when a text embedding model is used, and does not take effect when an image embedding model is used.

**Type:** [NetworkPolicy](arkts-arkdata-intelligence-networkpolicy-e.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ModelConfig-networkPolicy?: NetworkPolicy--><!--Device-ModelConfig-networkPolicy?: NetworkPolicy-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## version

```TypeScript
version: ModelVersion
```

Version of the model. The outputs of text or image embedding models with the same version are in the same vector space.

**Type:** [ModelVersion](arkts-arkdata-intelligence-modelversion-e.md)

**Since:** 15

<!--Device-ModelConfig-version: ModelVersion--><!--Device-ModelConfig-version: ModelVersion-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core
