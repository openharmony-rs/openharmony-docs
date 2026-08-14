# getImageEmbeddingModel

## getImageEmbeddingModel

```TypeScript
function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>
```

获取图像嵌入模型。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-intelligence-function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>--><!--Device-intelligence-function getImageEmbeddingModel(config: ModelConfig): Promise<ImageEmbedding>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | 是 | 嵌入模型的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ImageEmbedding](arkts-arkdata-intelligence-imageembedding-i.md)&gt; | Promise对象，返回图像嵌入模型，用于图像向量化。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; &lt;br&gt;2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

## 示例

ArkTS-Dyn示例：

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
    // 保存图像嵌入模型对象供后续使用
    imageEmbedding = data;
  })
  .catch((err: BusinessError) => {
    console.error(`Failed to get ImageModel. Code: ${err.code}, message: ${err.message}`);
  })
```

ArkTS-Sta示例：

```TypeScript
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

