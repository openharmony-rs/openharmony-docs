# createPlainTextData

## 导入模块

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## createPlainTextData

```TypeScript
function createPlainTextData(text: string): PasteData
```

构建一个纯文本剪贴板内容对象。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [createData](arkts-basicservices-pasteboard-createdata-f.md)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createPlainTextData(text: string): PasteData--><!--Device-pasteboard-function createPlainTextData(text: string): PasteData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 纯文本内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 剪贴板内容对象。 |

**示例**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('content');
```

