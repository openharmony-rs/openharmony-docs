# @ohos.data.intelligence (ArkData Intelligence Platform)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @my-2024-->
<!--Designer: @cuile44; @fysun17; @AnruiWang-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=7c57fe2e8c871d6c8a49dba383d3d523cb8ea605 translatedAt=2026-09-08T10:14:06.777Z pushedAt=2026-09-08T11:02:44.310Z -->

ArkData Intelligence Platform (AIP) provides application data vectorization, which leverages embedding models to convert multi-modal data such as unstructured text and images into semantic vectors.


> **NOTE**
>
> The initial APIs of this module are supported since API version 15. Updates will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```ts
import { intelligence } from '@kit.ArkData';
```

## intelligence.getTextEmbeddingModel

getTextEmbeddingModel(config: ModelConfig): Promise&lt;TextEmbedding&gt;

Obtains a text embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** Before API version 26.0.0, this API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801. Since API version 26.0.0, this API is supported on PCs/2-in-1 devices, phones, and tablets. On other devices, it returns error code 801.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| config | [ModelConfig](#modelconfig) | Yes  | Configuration of the embedded model to obtain.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;[TextEmbedding](#textembedding)&gt; | Promise used to return the text embedding model object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

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
    textEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error("Failed to get TextModel and code is " + err.code);
  })
```

## intelligence.getSupportedCloudModel

getSupportedCloudModel(): Promise&lt;Array&lt;CloudModelInfo&gt;&gt;

Obtains the supported cloud-side model information. This API uses a promise to return the result.

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API is supported on PCs/2-in-1 devices, phones, and tablets. On other devices, it returns error code 801.

**Model restriction**: This API can be used only in the stage model.

**Return value**

| Type                          | Description                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;[CloudModelInfo](#cloudmodelinfo)&gt;&gt; | Promise used to return the supported cloud-side model information. |

**Example**

```ts
intelligence.getSupportedCloudModel()
  .then((info: Array<intelligence.CloudModelInfo>) => {
    console.info("Succeeded in getting CloudModelInfo");
  });
```

## intelligence.getImageEmbeddingModel

getImageEmbeddingModel(config: ModelConfig): Promise&lt;ImageEmbedding&gt;

Obtains an image embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| config | [ModelConfig](#modelconfig) | Yes  | Configuration of the embedded model to obtain.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;[ImageEmbedding](#imageembedding)&gt; | Promise used to return the image embedding model object.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

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
    imageEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error("Failed to get ImageModel and code is " + err.code);
  })
```

## intelligence.splitText

splitText(text: string, config: SplitConfig): Promise&lt;Array&lt;string&gt;&gt;

Splits text. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences:** This API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| text | string | Yes  | Text to split, which can be any value.|
| config | [SplitConfig](#splitconfig) | Yes  | Configuration for splitting the text.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the blocks of the text.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

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
let splitText = 'text';

intelligence.splitText(splitText, splitConfig)
  .then((data: Array<string>) => {
    console.info("Succeeded in splitting Text");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to split Text and code is " + err.code);
  })
```

## ModelConfig

Represents the configuration an embedded model.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

| Name    | Type             | Read-Only| Optional| Description                                                        |
| ---------- | --------------------- | ----| ---- | ------------------------------------------------------------ |
| version    | [ModelVersion](#modelversion)           | No| No  |Version of the model.|
| isNpuAvailable | boolean                | No| No  | Whether to use the NPU to accelerate the vectorization process. The value **true** means to use the NPU, and the value **false** means the opposite. If this parameter is set to **true** but the device does not support NPUs, loading an embedding model will trigger error 31300000.|
| cachePath | string                | No | Yes | Local directory for model caching if the NPU is used. The value is in the /*xxx*/*xxx*/*xxx* format, for example, **/data**. The path cannot exceed 512 characters. <br>Default value: **""**|
| modelInfo    | [CloudModelInfo](#cloudmodelinfo)           | No | Yes   |Type and version information of the cloud-side model. It is configured when a text embedding model is used. Obtain the supported model information through the [getSupportedCloudModel](#intelligencegetsupportedcloudmodel) API. The default value is empty.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can only be used in the stage model. |
| networkPolicy    | [NetworkPolicy](#networkpolicy)           | No | Yes   |Network policy for downloading the cloud-side model. It is configured when a text embedding model is used. The default value is WIFI_ONLY.<br/>**Since:** 26.0.0<br/>**Model restriction:** This API can only be used in the stage model. |

## ModelVersion

Enumerates the model versions.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

| Name      | Value                  | Description                  |
| ---------- | ---------- | ---------------------- |
| BASIC_MODEL     | 0     | Basic embedding model version.  |

## CloudModelInfo

Defines the configuration information of the cloud-side model. It is configured when a cloud-side text vector model is used. You can obtain the cloud-side model information supported by the current device by calling [getSupportedCloudModel](#intelligencegetsupportedcloudmodel).

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Model restriction**: This API can be used only in the stage model.

| Name     | Type              | Read-only | Optional | Description                                                         |
| ---------- | --------------------- | ----| ---- | ------------------------------------------------------------ |
| modelType    |    string        | No | No   | Model type name, for example, "arkdata_text_embedding": cloud-side text vector model. |
| modelVersionCode | string                | No | Yes   | Model version. The default value is empty. |

## NetworkPolicy

Enumerates the network policies for downloading cloud-side models.

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.DataIntelligence.Core

**Model restriction**: This API can be used only in the stage model.

| Name       | Value         | Description      |
|----------|-----------|---------|
| WIFI_ONLY  | 0 | Downloads the model only over Wi-Fi.|
| WIFI_AND_CELLULAR  | 1 | Downloads the model over Wi-Fi and cellular networks. |

## Image

type Image = string

Represents the URI of an image, which is of the string type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Type                        | Description                 |
| ---------------------------- | --------------------- |
| string | Image URI, which cannot exceed 512 characters.|

## SplitConfig

Represents the configuration for text splitting.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

| Name    | Type             | Read-Only| Optional| Description                                                        |
| ---------- | --------------------- | ---- | ----| ------------------------------------------------------------ |
| size    |       number     | No  | No |Maximum size of a block. The value is a non-negative integer.|
| overlapRatio | number                | No | No  | Overlap ratio between adjacent blocks. <br>Value range: [0,1]<br>The value **0** indicates the lowest overlap ratio, and **1** indicates the highest overlap ratio.|


## TextEmbedding

Provides APIs for manipulating text embedding models.

Before calling any of the following APIs, you must obtain a **TextEmbedding** instance by using [intelligence.getTextEmbeddingModel](#intelligencegettextembeddingmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: This API is supported on phones, PCs/2-in-1 devices, and tablets. On other devices, it returns error code 801.

### loadModel

loadModel(): Promise&lt;void&gt;

Loads this text embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: Before API version 26.0.0, this API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801. Since API version 26.0.0, this API is supported on PCs/2-in-1 devices, phones, and tablets. On other devices, it returns error code 801.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textEmbedding.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to load Model and code is " + err.code);
  })
```

### releaseModel

releaseModel(): Promise&lt;void&gt;

Releases this text embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: Before API version 26.0.0, this API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801. Since API version 26.0.0, this API is supported on PCs/2-in-1 devices, phones, and tablets. On other devices, it returns error code 801.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textEmbedding.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to release Model and code is " + err.code);
  })
```

### getEmbedding

getEmbedding(text: string): Promise&lt;Array&lt;number&gt;&gt;

Obtains the embedding vector of the given text. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using [loadModel](#loadmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: Before API version 26.0.0, this API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801. Since API version 26.0.0, this API is supported on PCs/2-in-1 devices, phones, and tablets. On other devices, it returns error code 801.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| text | string | Yes  | Text for the embedding model, which cannot exceed 512 characters.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the vectorization result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textEmbedding.loadModel();
let text = 'text';
textEmbedding.getEmbedding(text)
  .then((data: Array<number>) => {
    console.info("Succeeded in getting Embedding");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to get Embedding and code is " + err.code);
  })
```

### getEmbedding

getEmbedding(batchTexts: Array&lt;string&gt;): Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt;

Obtains the embedding vector of a given batch of texts. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using [loadModel](#loadmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: Before API version 26.0.0, this API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801. Since API version 26.0.0, this API is supported on PCs/2-in-1 devices, phones, and tablets. On other devices, it returns error code 801.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| batchTexts | Array&lt;string&gt; | Yes  | Batch of texts, each of which cannot exceed 512 characters.|

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt; | Promise used to return the vectorization result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

textEmbedding.loadModel();
let batchTexts = ['text1', 'text2'];
textEmbedding.getEmbedding(batchTexts)
  .then((data: Array<Array<number>>) => {
    console.info("Succeeded in getting Embedding");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to get Embedding and code is " + err.code);
  })
```

## ImageEmbedding

Provides APIs for manipulating image embedding models.

Before calling any of the following APIs, you must obtain an **ImageEmbedding** instance by using [intelligence.getImageEmbeddingModel](#intelligencegetimageembeddingmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

### loadModel

loadModel(): Promise&lt;void&gt;

Loads this image embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: This API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageEmbedding.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to load Model and code is " + err.code);
  })
```

### releaseModel

releaseModel(): Promise&lt;void&gt;

Releases this image embedding model. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: This API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801.

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageEmbedding.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to release Model and code is " + err.code);
  })
```

### getEmbedding

getEmbedding(image: Image): Promise&lt;Array&lt;number&gt;&gt;

Obtains the embedding vector of the given image. This API uses a promise to return the result.

Before calling this API, ensure that an embedding model is successfully loaded by using [loadModel](#loadmodel).

**System capability**: SystemCapability.DistributedDataManager.DataIntelligence.Core

**Device behavior differences**: This API is supported on PCs/2-in-1 devices. On other devices, it returns error code 801.

**Parameters**

| Name      | Type                                   | Mandatory| Description                              |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| image | [Image](#image) | Yes | URI of the input image of the embedding model. |

**Return value**

| Type                         | Description                                |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;number&gt;&gt; | Promise used to return the vectorization result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [AIP Error Codes](errorcode-intelligence.md).

| **ID**| **Error Message**                                                                                                                                   |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

imageEmbedding.loadModel();
let image = 'file://<packageName>/data/storage/el2/base/haps/entry/files/xxx.jpg';
imageEmbedding.getEmbedding(image)
  .then((data: Array<number>) => {
    console.info("Succeeded in getting Embedding");
  })
  .catch((err: BusinessError) => {
    console.error("Failed to get Embedding and code is " + err.code);
  })
```