# @ohos.data.intelligence(ArkData Intelligence Platform)

Provides methods for intelligent data processing.

@namespace intelligence

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md) | Obtains an image embedding model. |
| [getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md) | Obtains the supported cloud embedding models. |
| [getTextEmbeddingModel](arkts-arkdata-intelligence-gettextembeddingmodel-f.md) | Obtains a text embedding model. |
| [splitText](arkts-arkdata-intelligence-splittext-f.md) | Splits text. |

### Interfaces

| Name | Description |
| --- | --- |
| [CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md) | Indicates cloud embedding model information. |
| [ImageEmbedding](arkts-arkdata-intelligence-imageembedding-i.md) | Describes the image embedding functions of the multi-modal embedding model. |
| [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | Manages configurations of the embedding model. |
| [SplitConfig](arkts-arkdata-intelligence-splitconfig-i.md) | Manages text chunk process configurations. |
| [TextEmbedding](arkts-arkdata-intelligence-textembedding-i.md) | Describes the text embedding functions of the multi-modal embedding model. Chinese and English are supported. |

### Enums

| Name | Description |
| --- | --- |
| [ModelVersion](arkts-arkdata-intelligence-modelversion-e.md) | Version of the model. |
| [NetworkPolicy](arkts-arkdata-intelligence-networkpolicy-e.md) | Indicates network policy. |

### Types

| Name | Description |
| --- | --- |
| [Image](arkts-arkdata-intelligence-image-t.md) | The type of the image can be its URI. |
