# getTextEmbeddingModel

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## getTextEmbeddingModel

```TypeScript
function getTextEmbeddingModel(config: ModelConfig): Promise<TextEmbedding>
```

获取文本嵌入模型。使用Promise异步回调。

**起始版本：** 23

<!--Device-intelligence-function getTextEmbeddingModel(config: ModelConfig): Promise<TextEmbedding>--><!--Device-intelligence-function getTextEmbeddingModel(config: ModelConfig): Promise<TextEmbedding>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [ModelConfig](arkts-arkdata-intelligence-modelconfig-i.md) | 是 | 嵌入模型的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[TextEmbedding](arkts-arkdata-intelligence-textembedding-i.md)&gt; | Promise对象，返回文本嵌入模型，用于文本向量化。 |

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

```TypeScript
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

