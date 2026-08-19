# createUriData

## 导入模块

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## createUriData

```TypeScript
function createUriData(uri: string): PasteData
```

构建一个URI剪贴板内容对象。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [createData](arkts-basicservices-pasteboard-createdata-f.md)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createUriData(uri: string): PasteData--><!--Device-pasteboard-function createUriData(uri: string): PasteData-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | URI内容，需符合标准URI格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | 剪贴板内容对象。 |

**示例**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createUriData('dataability:///com.example.myapplication1/user.txt');
```

