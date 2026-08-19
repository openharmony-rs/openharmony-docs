# ImageEmbedding(智慧数据平台)

描述多模态嵌入模型的图像嵌入函数。 下列接口都需先使用[intelligence.getImageEmbeddingModel](arkts-arkdata-intelligence-getimageembeddingmodel-f.md)获取到ImageEmbedding实例，再通过此实例 调用对应接口。

**起始版本：** 23

<!--Device-intelligence-interface ImageEmbedding--><!--Device-intelligence-interface ImageEmbedding-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getEmbedding

```TypeScript
getEmbedding(image: Image): Promise<Array<double>>
```

获取给定图像的嵌入向量。使用Promise异步回调。 该接口需先调用[loadModel](arkts-arkdata-intelligence-textembedding-i.md#loadmodel)加载嵌入模型，加载成功后调用getEmbedding。

**起始版本：** 23

<!--Device-ImageEmbedding-getEmbedding(image: Image): Promise<Array<double>>--><!--Device-ImageEmbedding-getEmbedding(image: Image): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| image | Image | 是 | 嵌入模型的输入图像类型的URI地址。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;double&gt;&gt; | Promise对象，返回向量化结果的数组对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; <br>2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
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

## loadModel

```TypeScript
loadModel(): Promise<void>
```

加载图像嵌入模型。使用Promise异步回调。 **配对调用：** - 调用loadModel()后，必须在使用完毕后调用[releaseModel()](#releasemodel)释放模型资源。 - 未调用releaseModel()会导致资源泄漏，影响系统性能。 - 建议将releaseModel()放在finally块中确保资源被正确释放。

**起始版本：** 23

<!--Device-ImageEmbedding-loadModel(): Promise<void>--><!--Device-ImageEmbedding-loadModel(): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
imageEmbedding?.loadModel()
  .then(() => {
    console.info("Succeeded in loading Model");
  })
  .catch((err) => {
    console.error(`Failed to load Model. Code: ${err.code}, message: ${err.message}`);
  })
```

## releaseModel

```TypeScript
releaseModel(): Promise<void>
```

释放图像嵌入模型。使用Promise异步回调。

**起始版本：** 23

<!--Device-ImageEmbedding-releaseModel(): Promise<void>--><!--Device-ImageEmbedding-releaseModel(): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

**示例**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
// imageEmbedding需先通过intelligence.getImageEmbeddingModel获取
imageEmbedding?.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```

