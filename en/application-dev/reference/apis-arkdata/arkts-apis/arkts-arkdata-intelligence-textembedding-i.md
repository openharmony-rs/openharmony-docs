# TextEmbedding

```TypeScript
interface TextEmbedding
```

Describes the text embedding function of the text embedding model.

Before calling any of the following APIs, you must obtain a **TextEmbedding** instance by using [getTextEmbeddingModel](arkts-arkdata-intelligence-gettextembeddingmodel-f.md)

**Device behavior differences:** This API can be properly called on PC/2-in-1, Phone, and Tablet devices. If it is called on other device types, error code 801 is returned.

**Since:** 15

<!--Device-intelligence-interface TextEmbedding--><!--Device-intelligence-interface TextEmbedding-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

## Modules to Import

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getEmbedding

```TypeScript
getEmbedding(text: string): Promise<Array<number>>
```

Obtains the embedding vector of the given text. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using loadModel.

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Since:** 15

<!--Device-TextEmbedding-getEmbedding(text: string): Promise<Array<double>>--><!--Device-TextEmbedding-getEmbedding(text: string): Promise<Array<double>>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Text for the embedding model, which cannot exceed 512 characters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the array of vectorization results. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain textEmbedding first via intelligence.getTextEmbeddingModel.
textEmbedding.loadModel()
  .then(() => {
    let text = 'text';
    textEmbedding.getEmbedding(text)
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

## getEmbedding

```TypeScript
getEmbedding(batchTexts: Array<string>): Promise<Array<Array<number>>>
```

Obtains the embedding vectors of a given batch of texts. Batch processing improves performance and is suitable for scenarios where multiple texts need to be processed simultaneously. This API uses a Promise to return the result asynchronously.

Before calling this API, ensure that an embedding model is successfully loaded by using loadModel

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Since:** 15

<!--Device-TextEmbedding-getEmbedding(batchTexts: Array<string>): Promise<Array<Array<double>>>--><!--Device-TextEmbedding-getEmbedding(batchTexts: Array<string>): Promise<Array<Array<double>>>-End-->

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| batchTexts | Array&lt;string&gt; | Yes | The input batch of texts of the embedding model. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt; | The promise used to return the embedding result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [31300000](../errorcode-intelligence.md#31300000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Obtain textEmbedding by calling intelligence.getTextEmbeddingModel first.
textEmbedding.loadModel()
  .then(() => {
    let batchTexts = ['text1', 'text2'];
    textEmbedding.getEmbedding(batchTexts)
      .then((data: Array<Array<number>>) => {
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

Loads this text embedding model. This API uses a promise to return the result.

**Paired call**  
- After calling **loadModel()**, you must call [releaseModel()](#releasemodel) to release the model resources  
when they are no longer needed.  
- Failure to call **releaseModel()** causes resource leakage and affects system performance.  
- It is recommended that **releaseModel()** be placed in a **finally** block to ensure that resources are  
properly released.

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Since:** 15

<!--Device-TextEmbedding-loadModel(): Promise<void>--><!--Device-TextEmbedding-loadModel(): Promise<void>-End-->

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

// Obtain textEmbedding first via intelligence.getTextEmbeddingModel.
textEmbedding.loadModel()
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

Releases this text embedding model. This API uses a promise to return the result.

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Since:** 15

<!--Device-TextEmbedding-releaseModel(): Promise<void>--><!--Device-TextEmbedding-releaseModel(): Promise<void>-End-->

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

// Obtain textEmbedding by calling intelligence.getTextEmbeddingModel first.
textEmbedding.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```
