# @ohos.data.intelligence (ArkData Intelligence Platform)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @my-2024-->
<!--Designer: @cuile44; @fysun17; @AnruiWang-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=a92c62906a53dbb211f0a7456ddb51494343703a translatedAt=2026-09-04T03:37:35.922Z pushedAt=2026-09-09T09:11:03.721Z -->

The ArkData Intelligence Platform (AIP) provides on-device intelligent data construction, enabling application data vectorization. It uses embedding models to convert multi-modal data such as unstructured text and images into semantic vectors. It applies to scenarios such as intelligent retrieval, content understanding, and similarity matching, helping developers solve the problem that unstructured data is difficult to compute and compare, and improving the processing efficiency and accuracy of applications in scenarios such as recommendation systems, intelligent Q&A, and image recognition.


> **NOTE**
>
> The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { intelligence } from '@kit.ArkData';
```

## intelligence.getTextEmbeddingModel

getTextEmbeddingModel(config: ModelConfig): Promise&lt;TextEmbedding&gt;

Obtains a text embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior Difference:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices, and returns error code 801 on other device types. Since API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices, and returns error code 801 on other device types.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| config | [ModelConfig](#modelconfig) | Yes  | Configuration of the embedded model to obtain.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;[TextEmbedding](#textembedding)&gt; | Promise object that returns the text embedding model for text vectorization. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

## intelligence.getSupportedCloudModel

getSupportedCloudModel(): Promise&lt;Array&lt;CloudModelInfo&gt;&gt;

Obtains the supported cloud model information. This API uses a promise to return the result.

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API can be properly called on PC/2-in-1, Phone, and Tablet devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                          | Description                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;[CloudModelInfo](#cloudmodelinfo)&gt;&gt; | Promise object, which returns the supported cloud model information. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

intelligence.getSupportedCloudModel()
  .then((info: Array<intelligence.CloudModelInfo>) => {
    console.info("Succeeded in getting CloudModelInfo");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get CloudModelInfo. Code: ${err.code}, message: ${err.message}`);
  });
```

## intelligence.getImageEmbeddingModel

getImageEmbeddingModel(config: ModelConfig): Promise&lt;ImageEmbedding&gt;

Obtains an image embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API can be properly called on PC/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| config | [ModelConfig](#modelconfig) | Yes  | Configuration of the embedded model to obtain.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;[ImageEmbedding](#imageembedding)&gt; | Promise object that returns the image embedding model for image vectorization. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

## intelligence.splitText

splitText(text: string, config: SplitConfig): Promise&lt;Array&lt;string&gt;&gt;

Splits text. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API can be properly called on PC/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| text | string | Yes | Text to be chunked. The maximum length of a single text is 100000 characters. An exception is thrown when the length exceeds the limit. |
| config | [SplitConfig](#splitconfig) | Yes  | Configuration for splitting the text.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;string&gt;&gt; | Promise object that returns an array of chunking results. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let splitConfig: intelligence.SplitConfig = {
  size: 10,
  overlapRatio: 0.1
}
let textToSplit = 'text';

intelligence.splitText(textToSplit, splitConfig)
  .then((data: Array<string>) => {
    console.info("Succeeded in splitting Text");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to split Text. Code: ${err.code}, message: ${err.message}`);
  })
```

## ModelConfig

Represents the configuration an embedded model.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

| Name    | Type             | Read-Only| Optional| Description                                                        |
| ---------- | --------------------- | ----| ---- | ------------------------------------------------------------ |
| version    | [ModelVersion](#modelversion)           | No| No  |Version of the model.|
| isNpuAvailable | boolean                | No| No  | Whether to use the NPU to accelerate the vectorization process. The value **true** means to use the NPU, and the value **false** means the opposite. If this parameter is set to **true** but the device does not support NPUs, loading an embedding model will trigger error 31300000.|
| cachePath | string                | No  | Yes  | If NPU is used for acceleration, a local path is required for model caching. The format is /xxx/xxx/xxx, where xxx is the path address, for example, "/data". The maximum length is 512 characters. The default value is "". An exception is thrown when the length exceeds the limit. |
| modelInfo    | [CloudModelInfo](#cloudmodelinfo)           | No | Yes   |Type and version information of the cloud-side model. Configure this parameter when a text embedding model is used. The supported model information is obtained through the [getSupportedCloudModel](#intelligencegetsupportedcloudmodel) API. The default value is empty.<br/>**Since:** 26.0.0<br/>**Model Constraint:** This API can be used only in the stage model. |
| networkPolicy | [NetworkPolicy](#networkpolicy) | No | Yes |Network policy used when downloading the cloud-side model. The default value is WIFI_ONLY. This parameter takes effect only when a text embedding model is used, and does not take effect when an image embedding model is used.<br/>**Since:** 26.0.0<br/>**Model Constraint:** This API can be used only in the stage model. |

## ModelVersion

Enumerates the model versions.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

| Name      | Value                  | Description                  |
| ---------- | ---------- | ---------------------- |
| BASIC_MODEL     | 0     | Basic embedding model version.  |

## CloudModelInfo

Defines the configuration information of the cloud-side model, which is configured when using the cloud-side text embedding model. You can obtain the cloud-side model information supported by the current device through [getSupportedCloudModel](#intelligencegetsupportedcloudmodel).

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Model restriction**: This API can be used only in the stage model.

| Name     | Type              | Read-only | Optional | Description                                                         |
| ---------- | --------------------- | ----| ---- | ------------------------------------------------------------ |
| modelType    |    string        | No | No   | Model type name, for example, "arkdata_text_embedding" indicates the cloud-side text embedding model. |
| modelVersionCode | string                | No | Yes   | Model version. The default value is empty. |

## NetworkPolicy

Enumerates the network policies for downloading cloud-side models.

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Model restriction**: This API can be used only in the stage model.

| Name       | Value         | Description      |
|----------|-----------|---------|
| WIFI_ONLY  | 0 | Download the model only over Wi-Fi. This policy applies to scenarios where mobile data traffic needs to be saved. |
| WIFI_AND_CELLULAR  | 1 | Download the model over both Wi-Fi and cellular networks. This policy applies to scenarios where the model needs to be obtained quickly and mobile data usage is allowed. |

## Image

type Image = string

Defines the URI of the image, which is a string.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type                        | Description                 |
| ---------------------------- | --------------------- |
| string | URI of the image. The maximum length is 512 characters. An exception is thrown when the length exceeds the limit. |

## SplitConfig

Represents the configuration for text splitting.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

| Name    | Type             | Read-Only| Optional| Description                                                        |
| ---------- | --------------------- | ---- | ----| ------------------------------------------------------------ |
| size | number | No | No | Maximum size of a chunk, which is a non-negative integer. A smaller size value is suitable for scenarios that require fine-grained chunking or have memory constraints, while a larger size value is suitable for reducing the number of chunks when processing large amounts of data. |
| overlapRatio | number | No | No | Overlap ratio between adjacent chunks. The value ranges from 0 to 1, where **0** indicates the lowest overlap ratio and **1** indicates the highest overlap ratio. A higher overlap ratio is suitable for long-text scenarios that require semantic continuity, while a lower ratio is suitable for short-text scenarios that require reduced duplicate computation. |


## TextEmbedding

Describes the text embedding function of the text embedding model.

Before calling any of the following APIs, you must obtain a **TextEmbedding** instance by using [intelligence.getTextEmbeddingModel](#intelligencegettextembeddingmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API can be properly called on PC/2-in-1, Phone, and Tablet devices. If it is called on other device types, error code 801 is returned.

### loadModel

loadModel(): Promise&lt;void&gt;

Loads this text embedding model. This API uses a promise to return the result.

**Paired call**
- After calling **loadModel()**, you must call [releaseModel()](#releasemodel) to release the model resources when they are no longer needed.
- Failure to call **releaseModel()** causes resource leakage and affects system performance.
- It is recommended that **releaseModel()** be placed in a **finally** block to ensure that resources are properly released.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

### releaseModel

releaseModel(): Promise&lt;void&gt;

Releases this text embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

### getEmbedding

getEmbedding(text: string): Promise&lt;Array&lt;number&gt;&gt;

Obtains the embedding vector of the given text. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using [loadModel](#loadmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| text | string | Yes  | Text for the embedding model, which cannot exceed 512 characters.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the array of vectorization results. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

### getEmbedding

getEmbedding(batchTexts: Array&lt;string&gt;): Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt;

Obtains the embedding vectors of a given batch of texts. Batch processing improves performance and is suitable for scenarios where multiple texts need to be processed simultaneously. This API uses a Promise to return the result asynchronously.

Before calling this API, ensure that an embedding model is successfully loaded by using [loadModel](#loadmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** Before API version 26.0.0, this API can be called normally on PC/2in1 devices and returns error code 801 on other device types. Starting from API version 26.0.0, this API can be called normally on PC/2in1, Phone, and Tablet devices and returns error code 801 on other device types.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| batchTexts | Array&lt;string&gt; | Yes  | Batch of texts, each of which cannot exceed 512 characters.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt; | Promise object that returns a two-dimensional array of batch vectorization results. |

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

## ImageEmbedding

Provides APIs for manipulating image embedding models.

Before calling any of the following APIs, you must obtain an **ImageEmbedding** instance by using [intelligence.getImageEmbeddingModel](#intelligencegetimageembeddingmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

### loadModel

loadModel(): Promise&lt;void&gt;

Loads this image embedding model. This API uses a promise to return the result.

**Paired call**
- After calling **loadModel()**, you must call [releaseModel()](#releasemodel-1) to release the model resources when they are no longer needed.
- Failure to call **releaseModel()** causes resource leakage and affects system performance.
- It is recommended that **releaseModel()** be placed in a **finally** block to ensure that resources are released correctly.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** This API can be called normally on PC/2in1 devices and returns error code 801 on other device types.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

### releaseModel

releaseModel(): Promise&lt;void&gt;

Releases this image embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** This API can be called normally on PC/2in1 devices and returns error code 801 on other device types.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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

### getEmbedding

getEmbedding(image: Image): Promise&lt;Array&lt;number&gt;&gt;

Obtains the embedding vector of the given image. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using [loadModel](#loadmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device Behavior:** This API can be called normally on PC/2in1 devices, and returns error code 801 on other device types.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| image | [Image](#image) | Yes | URI of the input image for the embedding model. |

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the vectorization result.|

**Error codes**

For details about the error codes, see [Common Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
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