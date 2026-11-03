# ImageEmbedding

```TypeScript
interface ImageEmbedding
```

Provides APIs for manipulating image embedding models. Before calling any of the following APIs, you must obtain an **ImageEmbedding** instance by using [getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md)

**Since:** 15

<!--Device-intelligence-interface ImageEmbedding--><!--Device-intelligence-interface ImageEmbedding-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getEmbedding

```TypeScript
getEmbedding(image: Image): Promise<Array<number>>
```

Obtains the embedding vector of the given image. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using loadModel

**Device Behavior:** This API can be called normally on PC/2in1 devices, and returns error code 801 on other device types.

**Since:** 15

<!--Device-ImageEmbedding-getEmbedding(image: Image): Promise<Array<double>>--><!--Device-ImageEmbedding-getEmbedding(image: Image): Promise<Array<double>>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| image | [Image](arkts-arkdata-intelligence-image-t.md) | Yes | URI of the input image for the embedding model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the vectorization result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
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

Loads this image embedding model. This API uses a promise to return the result.

**Paired call**  
- After calling **loadModel()**, you must call [releaseModel()](#releasemodel) to release the model resources  
when they are no longer needed.  
- Failure to call **releaseModel()** causes resource leakage and affects system performance.  
- It is recommended that **releaseModel()** be placed in a **finally** block to ensure that resources are  
released correctly.

**Device Behavior:** This API can be called normally on PC/2in1 devices and returns error code 801 on other device types.

**Since:** 15

<!--Device-ImageEmbedding-loadModel(): Promise<void>--><!--Device-ImageEmbedding-loadModel(): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
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

Releases this image embedding model. This API uses a promise to return the result.

**Device Behavior:** This API can be called normally on PC/2in1 devices and returns error code 801 on other device types.

**Since:** 15

<!--Device-ImageEmbedding-releaseModel(): Promise<void>--><!--Device-ImageEmbedding-releaseModel(): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
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
