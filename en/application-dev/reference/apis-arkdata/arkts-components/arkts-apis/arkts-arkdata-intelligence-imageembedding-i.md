# ImageEmbedding

```TypeScript
interface ImageEmbedding
```

Describes the image embedding functions of the multi-modal embedding model.

@interface ImageEmbedding

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getEmbedding

```TypeScript
getEmbedding(image: Image): Promise<Array<number>>
```

Obtains the embedding vector of the given image. The model can handle images below 20 MB in size in a single inference.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [Image](arkts-arkdata-intelligence-image-t.md) | Yes | The input image of the embedding model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | The promise used to return the embedding result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain imageEmbedding by calling intelligence.getImageEmbeddingModel first.
imageEmbedding.loadModel().then(() => {
  let image = 'file://<packageName>/data/storage/el2/base/haps/entry/files/xxx.jpg';
  imageEmbedding.getEmbedding(image)
    .then((data: Array<number>) => {
      console.info("Succeeded in getting Embedding");
    })
    .catch((err: BusinessError) => {
      console.error(`Failed to get Embedding. Code: ${err.code}, message: ${err.message}`);
    })
}).catch((err: BusinessError) => {
  console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
})
```

## loadModel

```TypeScript
loadModel(): Promise<void>
```

Loads this image embedding model. If the loading fails, an error code is returned.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain imageEmbedding by calling intelligence.getImageEmbeddingModel first.
imageEmbedding.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

## releaseModel

```TypeScript
releaseModel(): Promise<void>
```

Releases this image embedding model. If the releasing fails, an error code is returned.

**Since:** 15

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain imageEmbedding by calling intelligence.getImageEmbeddingModel first.
imageEmbedding.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```
