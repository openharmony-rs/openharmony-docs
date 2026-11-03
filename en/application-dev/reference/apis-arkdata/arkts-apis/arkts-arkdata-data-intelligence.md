# @ohos.data.intelligence(ArkData Intelligence Platform)

The ArkData Intelligence Platform (AIP) provides on-device intelligent data construction, enabling application data vectorization. It uses embedding models to convert multi-modal data such as unstructured text and images into semantic vectors. It applies to scenarios such as intelligent retrieval, content understanding, and similarity matching, helping developers solve the problem that unstructured data is difficult to compute and compare, and improving the processing efficiency and accuracy of applications in scenarios such as recommendation systems, intelligent Q&A, and image recognition.

> **NOTE:** 
> 
> The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.

**Since:** 15

<!--Device-unnamed-declare namespace intelligence--><!--Device-unnamed-declare namespace intelligence-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md#getimageembeddingmodel-1) | Obtains an image embedding model. This API uses a promise to return the result. |
| [getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md#getsupportedcloudmodel-1) | Obtains the supported cloud model information. This API uses a promise to return the result. |
| [getTextEmbeddingModel](arkts-arkdata-intelligence-gettextembeddingmodel-f.md#gettextembeddingmodel-1) | Obtains a text embedding model. This API uses a promise to return the result. |
| [splitText](arkts-arkdata-intelligence-splittext-f.md#splittext-1) | Splits text. This API uses a promise to return the result. |

### Interfaces

| Name | Description |
| --- | --- |
| [CloudModelInfo](arkts-arkdata-intelligence-cloudmodelinfo-i.md) | Defines the configuration information of the cloud-side model, which is configured when using the cloud-side text embedding model. You can obtain the cloud-side model information supported by the current device through [getSupportedCloudModel](arkts-arkdata-intelligence-getsupportedcloudmodel-f.md). |
| [ImageEmbedding](arkts-arkdata-intelligence-imageembedding-i.md) | Provides APIs for manipulating image embedding models. Before calling any of the following APIs, you must obtain an **ImageEmbedding** instance by using [getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md) |
| [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | Represents the configuration an embedded model. |
| [SplitConfig](arkts-arkdata-intelligence-splitconfig-i.md) | Represents the configuration for text splitting. |
| [TextEmbedding](arkts-arkdata-intelligence-textembedding-i.md) | Describes the text embedding function of the text embedding model. |

### Types

| Name | Description |
| --- | --- |
| [Image](arkts-arkdata-intelligence-image-t.md) | Defines the URI of the image, which is a string. URI of the image. The maximum length is 512 characters. An exception is thrown when the length exceeds the limit. |

### Enums

| Name | Description |
| --- | --- |
| [ModelVersion](arkts-arkdata-intelligence-modelversion-e.md) | Version of the model. |
| [NetworkPolicy](arkts-arkdata-intelligence-networkpolicy-e.md) | Enumerates the network policies for downloading cloud-side models. |
