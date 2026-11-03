# getImageEmbeddingModel

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getImageEmbeddingModel

```TypeScript
function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>
```

Obtains an image embedding model. This API uses a promise to return the result.

**Device behavior differences:** This API can be properly called on PC/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Since:** 15

<!--Device-intelligence-function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>--><!--Device-intelligence-function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | Yes | Configuration of the embedded model to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ImageEmbedding](arkts-arkdata-intelligence-imageembedding-i.md)&gt; | Promise used to return the image embedding model for image vectorization. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let imageConfig: intelligence.ModelConfig = {
  version: intelligence.ModelVersion.BASIC_MODEL,
  isNpuAvailable: false,
  cachePath: "/data"
}
let imageEmbedding: intelligence.ImageEmbedding;

intelligence.getImageEmbeddingModel(imageConfig)
  .then((data: intelligence.ImageEmbedding) => {
    console.info("Succeeded in getting ImageModel");
    // Save the image embedding model object for later use.
    imageEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get ImageModel. Code: ${err.code}, message: ${err.message}`);
  })
```
