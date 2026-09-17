# getImageEmbeddingModel

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getImageEmbeddingModel

```TypeScript
function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>
```

Obtains an image embedding model.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | Yes | The configuration of the embedding model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ImageEmbedding](arkts-arkdata-intelligence-imageembedding-i.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
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
