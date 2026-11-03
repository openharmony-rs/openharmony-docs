# CloudModelInfo

```TypeScript
interface CloudModelInfo
```

Defines the configuration information of the cloud-side model, which is configured when using the cloud-side text embedding model. You can obtain the cloud-side model information supported by the current device through [getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md).

**Since:** 26.0.0

<!--Device-intelligence-interface CloudModelInfo--><!--Device-intelligence-interface CloudModelInfo-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## modelType

```TypeScript
modelType: string
```

Model type name, for example, "arkdata_text_embedding" indicates the cloud-side text embedding model.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudModelInfo-modelType: string--><!--Device-CloudModelInfo-modelType: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## modelVersionCode

```TypeScript
modelVersionCode?: string
```

Model version. The default value is empty.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-CloudModelInfo-modelVersionCode?: string--><!--Device-CloudModelInfo-modelVersionCode?: string-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core
