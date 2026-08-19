# splitText

## 导入模块

```TypeScript
import { intelligence } from '@kit.ArkData';
```

## splitText

```TypeScript
function splitText(text: string, config: SplitConfig): Promise<Array<string>>
```

获取文本的分块。使用Promise异步回调。

**起始版本：** 23

<!--Device-intelligence-function splitText(text: string, config: SplitConfig): Promise<Array<string>>--><!--Device-intelligence-function splitText(text: string, config: SplitConfig): Promise<Array<string>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataIntelligence.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 待分块的文本。单个文本长度上限为100000个字符。超出长度时抛出异常。 |
| config | [SplitConfig](arkts-arkdata-intelligence-splitconfig-i.md) | 是 | 文本分块的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise对象，返回分块结果的数组。 |

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

```TypeScript
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

