# getTextEmbeddingModel

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getTextEmbeddingModel

```TypeScript
function getTextEmbeddingModel(config: ModelConfig): Promise<TextEmbedding>
```

Obtains a text embedding model. This API uses a promise to return the result.

**Device Behavior Difference:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices, and returns error code 801 on other device types. Since API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices, and returns error code 801 on other device types.

**Since:** 15

<!--Device-intelligence-function getTextEmbeddingModel(config: ModelConfig): Promise<TextEmbedding>--><!--Device-intelligence-function getTextEmbeddingModel(config: ModelConfig): Promise<TextEmbedding>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | Yes | Configuration of the embedded model to obtain. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TextEmbedding](arkts-arkdata-intelligence-textembedding-i.md)&gt; | Promise used to return the text embedding model for text vectorization. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | [Sync] Parameter error. Possible causes: <br>1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types; <br>3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let textConfig: intelligence.ModelConfig = {
  version: intelligence.ModelVersion.BASIC_MODEL,
  isNpuAvailable: false,
  cachePath: "/data"
}
let textEmbedding: intelligence.TextEmbedding;

intelligence.getTextEmbeddingModel(textConfig)
  .then((data: intelligence.TextEmbedding) => {
    console.info("Succeeded in getting TextModel");
    // Save the text embedding model object for later use.
    textEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get TextModel. Code: ${err.code}, message: ${err.message}`);
  })
```
