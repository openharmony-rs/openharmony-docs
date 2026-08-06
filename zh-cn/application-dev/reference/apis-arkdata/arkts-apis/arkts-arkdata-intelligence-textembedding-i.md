# TextEmbedding

描述文本嵌入模型的文本嵌入函数。 下列接口都需先使用[intelligence.getTextEmbeddingModel]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_获取到TextEmbedding实例，再通过此实例调用对 应接口。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-intelligence-interface TextEmbedding--><!--Device-intelligence-interface TextEmbedding-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

## getEmbedding

ArkTS-Dyn:
```TypeScript
getEmbedding(text: string): Promise<Array<number>>
```

ArkTS-Sta:
```TypeScript
getEmbedding(text: string): Promise<Array<double>>
```

获取给定文本的嵌入向量。使用Promise异步回调。 该接口需先调用[loadModel]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_加载嵌入模型，加载成功后调用getEmbedding。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-TextEmbedding-getEmbedding(text: string): Promise<Array<double>>--><!--Device-TextEmbedding-getEmbedding(text: string): Promise<Array<double>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 嵌入模型的输入文本。长度上限为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;Array&lt;number&gt;&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;Array&lt;double&gt;&gt; | Promise对象，返回向量化结果的数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
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

## getEmbedding

ArkTS-Dyn:
```TypeScript
getEmbedding(batchTexts: Array<string>): Promise<Array<Array<number>>>
```

ArkTS-Sta:
```TypeScript
getEmbedding(batchTexts: Array<string>): Promise<Array<Array<double>>>
```

获取给定批次文本的嵌入向量。批量处理可以提高性能，适用于需要同时处理多个文本的场景。使用Promise异步回调。 该接口需先调用[loadModel]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_加载嵌入模型，加载成功后调用getEmbedding。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-TextEmbedding-getEmbedding(batchTexts: Array<string>): Promise<Array<Array<double>>>--><!--Device-TextEmbedding-getEmbedding(batchTexts: Array<string>): Promise<Array<Array<double>>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| batchTexts | Array&lt;string&gt; | 是 | 嵌入模型的文本输入批次。单个文本长度上限为512个字符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArkTS-Dyn: Promise&lt;Array&lt;Array&lt;number&gt;&gt;&gt;  \_\_\_HTML\_TAG\_USD\_0\_\_\_ArkTS-Sta：Promise&lt;Array&lt;Array&lt;double&gt;&gt;&gt; | Promise对象，返回批次向量化结果的二维数组。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
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

## loadModel

```TypeScript
loadModel(): Promise<void>
```

加载文本嵌入模型。使用Promise异步回调。 **配对调用：** - 调用loadModel()后，必须在使用完毕后调用\_\_\_MD\_LINK\_DESC\_USD\_0\_\_\_释放模型资源。 - 未调用releaseModel()会导致资源泄漏，影响系统性能。 - 建议将releaseModel()放在finally块中确保资源被正确释放。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-TextEmbedding-loadModel(): Promise<void>--><!--Device-TextEmbedding-loadModel(): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [31300000](../errorcode-intelligence.md#31300000-服务内部异常) | Inner error. |

**示例：**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
textEmbedding?.loadModel()
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

释放文本嵌入模型。使用Promise异步回调。

**起始版本：** 15

**ArkTS模式：** ArkTS-Dyn起始版本为15；ArkTS-Sta起始版本为23。

<!--Device-TextEmbedding-releaseModel(): Promise<void>--><!--Device-TextEmbedding-releaseModel(): Promise<void>-End-->

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

**示例：**

ArkTS-Dyn示例：

```TypeScript
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

```TypeScript
// textEmbedding需先通过intelligence.getTextEmbeddingModel获取
textEmbedding?.releaseModel()
  .then(() => {
    console.info("Succeeded in releasing Model");
  })
  .catch((err) => {
    console.error(`Failed to release Model. Code: ${err.code}, message: ${err.message}`);
  })
```

