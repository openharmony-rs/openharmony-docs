# @ohos.data.intelligence (智慧数据平台)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @my-2024-->
<!--Designer: @cuile44; @fysun17; @AnruiWang-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

智慧数据平台（ArkData Intelligence Platform，AIP）提供端侧数据智慧化构建，使应用数据向量化，通过嵌入模型将非结构化的文本、图像等多模态数据，转换成具有语义的向量。适用于智能检索、内容理解、相似度匹配等场景，帮助开发者解决非结构化数据难以计算和比较的问题，提升应用在推荐系统、智能问答、图像识别等场景下的处理效率和准确性。


> **说明：**
>
> 本模块同时支持ArkTS-Dyn、ArkTS-Sta。
>
> 本模块首批接口从API version 15开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> 考虑到数据向量化处理的计算量和资源占用较大，当前仅支持在PC/2in1设备上使用。


## 导入模块

```ts
import { intelligence } from '@kit.ArkData';
```

## intelligence.getTextEmbeddingModel

getTextEmbeddingModel(config: ModelConfig): Promise&lt;TextEmbedding&gt;

获取文本嵌入模型。使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 在API版本26.0.0之前，该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码；从API版本26.0.0开始，该接口在PC/2in1、Phone和Tablet设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                               |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| config | [ModelConfig](#modelconfig) | 是   | 嵌入模型的配置信息。 |

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;[TextEmbedding](#textembedding)&gt; | Promise对象，返回文本嵌入模型，用于文本向量化。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

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
    // 保存文本嵌入模型对象供后续使用
    textEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get TextModel. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```ts
let textConfig: intelligence.ModelConfig = {
  version: intelligence.ModelVersion.BASIC_MODEL,
  isNpuAvailable: false,
  cachePath: "/data"
}
let textEmbedding: intelligence.TextEmbedding | null = null;

intelligence.getTextEmbeddingModel(textConfig)
  .then((data: intelligence.TextEmbedding) => {
    console.info("Succeeded in getting TextModel");
    // 保存文本嵌入模型对象供后续使用
    textEmbedding = data;
  })
  .catch((err) => {
    console.error(`Failed to get TextModel. Code: ${err.code}, message: ${err.message}`);
  })
```

## intelligence.getSupportedCloudModel

getSupportedCloudModel(): Promise&lt;Array&lt;CloudModelInfo&gt;&gt;

获取支持的云侧模型信息。使用Promise异步回调。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 该接口在PC/2in1、Phone和Tablet设备中可正常调用，在其他设备类型中返回801错误码。

**模型约束：** 此接口仅可在Stage模型下使用。

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;[CloudModelInfo](#cloudmodelinfo)&gt;&gt; | Promise对象，返回支持的云侧模型信息。 |

**示例：**

```ts
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

获取图像嵌入模型。使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                               |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| config | [ModelConfig](#modelconfig) | 是   | 嵌入模型的配置信息。 |

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;[ImageEmbedding](#imageembedding)&gt; | Promise对象，返回图像嵌入模型，用于图像向量化。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

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
    // 保存图像嵌入模型对象供后续使用
    imageEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get ImageModel. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```ts
let imageConfig: intelligence.ModelConfig = {
  version: intelligence.ModelVersion.BASIC_MODEL,
  isNpuAvailable: false,
  cachePath: "/data"
}
let imageEmbedding: intelligence.ImageEmbedding | null = null;

intelligence.getImageEmbeddingModel(imageConfig)
  .then((data: intelligence.ImageEmbedding) => {
    console.info("Succeeded in getting ImageModel");
    // 保存图像嵌入模型对象供后续使用
    imageEmbedding = data;
  })
  .catch((err) => {
    console.error(`Failed to get ImageModel. Code: ${err.code}, message: ${err.message}`);
  })
```

## intelligence.splitText

splitText(text: string, config: SplitConfig): Promise&lt;Array&lt;string&gt;&gt;

获取文本的分块。使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                               |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| text | string | 是   | 待分块的文本。单个文本长度上限为100000个字符。超出长度时抛出异常。 |
| config | [SplitConfig](#splitconfig) | 是   | 文本分块的配置信息。 |

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回分块结果的数组。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

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

ArkTS-Sta示例：

```ts
let splitConfig: intelligence.SplitConfig = {
  size: 10,
  overlapRatio: 0.1
}
let textToSplit = 'text';

intelligence.splitText(textToSplit, splitConfig)
  .then((data: Array<string>) => {
    console.info("Succeeded in splitting Text");
  })
  .catch((err) => {
    console.error(`Failed to split Text. Code: ${err.code}, message: ${err.message}`);
  })
```

## ModelConfig

管理嵌入模型的配置信息。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 名称     | 类型              | 只读 | 可选| 说明                                                         |
| ---------- | --------------------- | ----| ---- | ------------------------------------------------------------ |
| version    | [ModelVersion](#modelversion)           | 否 | 否   |模型的版本。 |
| isNpuAvailable | boolean                | 否 | 否   | 指示是否使用NPU加速向量化过程，true表示使用，false表示不使用。如果设备不支持NPU，调用加载模型会失败，并抛出错误码31300000。 |
| cachePath | string                | 否  | 是  | 如果使用NPU进行加速，则需要本地路径进行模型缓存。格式为/xxx/xxx/xxx，xxx为路径地址，例如"/data"。长度上限为512个字符。默认值为""。超出长度时抛出异常。 |
| modelInfo    | [CloudModelInfo](#cloudmodelinfo)           | 否 | 是   |云侧模型类型和版本信息，在使用文本向量模型时配置，通过[getSupportedCloudModel](#intelligencegetsupportedcloudmodel)接口获取支持的模型信息，默认值为空。<br/>**ArkTS-Dyn起始版本：** 26.0.0<br/>**ArkTS-Sta起始版本：** 26.0.0<br/>**模型约束：** 此接口仅可在Stage模型下使用。 |
| networkPolicy    | [NetworkPolicy](#networkpolicy)           | 否 | 是   |下载云侧模型时使用的网络策略，默认值为WIFI_ONLY。此参数仅在使用文本嵌入模型时生效，在使用图像嵌入模型场景此参数不生效。<br/>**ArkTS-Dyn起始版本：** 26.0.0<br/>**ArkTS-Sta起始版本：** 26.0.0**模型约束：** 此接口仅可在Stage模型下使用。 |

## ModelVersion

模型版本枚举。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 名称       | 值                   | 说明                   |
| ---------- | ---------- | ---------------------- |
| BASIC_MODEL     | 0     | 基本嵌入模型版本。   |

## CloudModelInfo

云侧模型的配置信息，在使用云侧文本向量模型时配置，可通过[getSupportedCloudModel](#intelligencegetsupportedcloudmodel)接口获取当前设备支持的云侧模型信息。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称     | 类型              | 只读 | 可选| 说明                                                         |
| ---------- | --------------------- | ----| ---- | ------------------------------------------------------------ |
| modelType    |    string        | 否 | 否   |模型类型名称，如"arkdata_text_embedding"表示云侧文本向量模型。 |
| modelVersionCode | string                | 否 | 是   | 模型版本，默认值为空。 |

## NetworkPolicy

下载云侧模型的网络策略枚举。

**ArkTS-Dyn起始版本：** 26.0.0

**ArkTS-Sta起始版本：** 26.0.0

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**模型约束：** 此接口仅可在Stage模型下使用。

| 名称       | 值         | 说明      |
|----------|-----------|---------|
| WIFI_ONLY  | 0 | 仅在Wi-Fi状态下下载模型，适用于需要节省移动数据流量的场景。|
| WIFI_AND_CELLULAR  | 1 | 在Wi-Fi和蜂窝网络状态下下载模型，适用于需要快速获取模型且允许使用移动数据的场景。 |

## Image

type Image = string

表示图片的URI地址，为string类型。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 类型                         | 说明                  |
| ---------------------------- | --------------------- |
| string | 图片的URI地址。长度上限为512个字符。超出长度时抛出异常。 |

## SplitConfig

管理文本分块的配置信息。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

| 名称     | 类型              | 只读 | 可选 | 说明                                                         |
| ---------- | --------------------- | ---- | ----| ------------------------------------------------------------ |
| size    |       number     | 否   | 否  |分块的最大大小，取值为非负整数。较小的size值适用于需要精细化分块或处理内存受限场景，较大的size值适用于处理大数据量时减少分块数量。 |
| overlapRatio | number                | 否  | 否   | 相邻分块之间的重叠比率。范围为[0,1]，0表示重叠比率最低，1表示重叠比率最高。较高的重叠比率适用于需要保持语义连贯性的长文本场景，较低的比率适用于需要减少重复计算的短文本场景。 |


## TextEmbedding

描述文本嵌入模型的文本嵌入函数。

下列接口都需先使用[intelligence.getTextEmbeddingModel](#intelligencegettextembeddingmodel)获取到TextEmbedding实例，再通过此实例调用对应接口。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

### loadModel

loadModel(): Promise&lt;void&gt;

加载文本嵌入模型。使用Promise异步回调。

**配对调用：**
- 调用loadModel()后，必须在使用完毕后调用[releaseModel()](#releasemodel)释放模型资源。
- 未调用releaseModel()会导致资源泄漏，影响系统性能。
- 建议将releaseModel()放在finally块中确保资源被正确释放。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 在API版本26.0.0之前，该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码；从API版本26.0.0开始，该接口在PC/2in1、Phone和Tablet设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
textEmbedding.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```ts
// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
textEmbedding?.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

### releaseModel

releaseModel(): Promise&lt;void&gt;

释放文本嵌入模型。使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 在API版本26.0.0之前，该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码；从API版本26.0.0开始，该接口在PC/2in1、Phone和Tablet设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
textEmbedding.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```ts
// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
textEmbedding?.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```

### getEmbedding

ArkTS-Dyn: getEmbedding(text: string): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: getEmbedding(text: string): Promise&lt;Array&lt;double&gt;&gt;

获取给定文本的嵌入向量。使用Promise异步回调。

该接口需先调用[loadModel](#loadmodel)加载嵌入模型，加载成功后调用getEmbedding。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 在API版本26.0.0之前，该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码；从API版本26.0.0开始，该接口在PC/2in1、Phone和Tablet设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                               |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| text | string | 是   | 嵌入模型的输入文本。长度上限为512个字符。 |

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt; | Promise对象，返回向量化结果的数组。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
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

ArkTS-Sta示例：

```ts
textEmbedding?.loadModel()
  .then(() => {
    let text = 'text';
    textEmbedding?.getEmbedding(text)
      .then((data: Array<number>) => {
        console.info("Succeeded in getting Embedding");
      })
      .catch((err) => {
        console.error(`Failed to get Embedding. Code: ${err.code}, message: ${err.message}`);
      })
  }).catch((err) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

### getEmbedding

ArkTS-Dyn: getEmbedding(batchTexts: Array&lt;string&gt;): Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt;

ArkTS-Sta: getEmbedding(batchTexts: Array&lt;string&gt;): Promise&lt;Array&lt;Array&lt;double&gt;&gt;&gt;

获取给定批次文本的嵌入向量。批量处理可以提高性能，适用于需要同时处理多个文本的场景。使用Promise异步回调。

该接口需先调用[loadModel](#loadmodel)加载嵌入模型，加载成功后调用getEmbedding。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 在API版本26.0.0之前，该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码；从API版本26.0.0开始，该接口在PC/2in1、Phone和Tablet设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                               |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| batchTexts | Array&lt;string&gt; | 是   | 嵌入模型的文本输入批次。单个文本长度上限为512个字符。 |

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| ArkTS-Dyn: Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;Array&lt;double&gt;&gt;&gt; | Promise对象，返回批次向量化结果的二维数组。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
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

ArkTS-Sta示例：

```ts
textEmbedding?.loadModel()
  .then(() => {
    let batchTexts = ['text1', 'text2'];
    textEmbedding?.getEmbedding(batchTexts)
      .then((data: Array<Array<double>>) => {
        console.info("Succeeded in getting Embedding");
      })
      .catch((err) => {
        console.error(`Failed to get Embedding. Code: ${err.code}, message: ${err.message}`);
      })
  }).catch((err) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

## ImageEmbedding

描述多模态嵌入模型的图像嵌入函数。

下列接口都需先使用[intelligence.getImageEmbeddingModel](#intelligencegetimageembeddingmodel)获取到ImageEmbedding实例，再通过此实例调用对应接口。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

### loadModel

loadModel(): Promise&lt;void&gt;

加载图像嵌入模型。使用Promise异步回调。

 **配对调用：**
- 调用loadModel()后，必须在使用完毕后调用[releaseModel()](#releasemodel-1)释放模型资源。
- 未调用releaseModel()会导致资源泄漏，影响系统性能。
- 建议将releaseModel()放在finally块中确保资源被正确释放。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
imageEmbedding.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```ts
// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
imageEmbedding?.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

### releaseModel

releaseModel(): Promise&lt;void&gt;

释放图像嵌入模型。使用Promise异步回调。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
imageEmbedding.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```ts
// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
imageEmbedding?.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```

### getEmbedding

ArkTS-Dyn: getEmbedding(image: Image): Promise&lt;Array&lt;number&gt;&gt;

ArkTS-Sta: getEmbedding(image: Image): Promise&lt;Array&lt;double&gt;&gt;

获取给定图像的嵌入向量。使用Promise异步回调。

该接口需先调用[loadModel](#loadmodel)加载嵌入模型，加载成功后调用getEmbedding。

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**设备行为差异：** 该接口在PC/2in1设备中可正常调用，在其他设备类型中返回801错误码。

**ArkTS-Dyn起始版本：** 15

**ArkTS-Sta起始版本：** 23

**参数：**

| 参数名       | 类型                                    | 必填 | 说明                               |
| ------------ | --------------------------------------- | ---- | :--------------------------------- |
| image | [Image](#image) | 是   | 嵌入模型的输入图像类型的URI地址。 |

**返回值：**

| 类型                          | 说明                                 |
| ----------------------------- | ------------------------------------ |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;<br>ArkTS-Sta: Promise&lt;Array&lt;double&gt;&gt; | Promise对象，返回向量化结果的数组对象。 |

**错误码：**

以下错误码的详细介绍请参见[通用错误码](../errorcode-universal.md)和[智慧数据平台错误码](errorcode-intelligence.md)。

| **错误码ID** | **错误信息**                                                                                                                                    |
| ------------ | ----------------------------------------------------------------------------------------------------------------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| 801          | Capability not supported. |
| 31300000     | Inner error. |

**示例：**

ArkTS-Dyn示例：

```ts
import { BusinessError } from '@kit.BasicServicesKit';

// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
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

ArkTS-Sta示例：

```ts
imageEmbedding?.loadModel().then(() => {
  let image = 'file://<packageName>/data/storage/el2/base/haps/entry/files/xxx.jpg';
  imageEmbedding?.getEmbedding(image)
    .then((data: Array<double>) => {
      console.info("Succeeded in getting Embedding");
    })
    .catch((err) => {
      console.error(`Failed to get Embedding. Code: ${err.code}, message: ${err.message}`);
    })
}).catch((err) => {
  console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
})
```