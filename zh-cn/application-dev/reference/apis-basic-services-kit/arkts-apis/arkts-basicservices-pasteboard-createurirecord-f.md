# createUriRecord

## 导入模块

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## createUriRecord

```TypeScript
function createUriRecord(uri: string): PasteDataRecord
```

创建一条URI内容的条目。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [createRecord](arkts-basicservices-pasteboard-createrecord-f.md)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createUriRecord(uri: string): PasteDataRecord--><!--Device-pasteboard-function createUriRecord(uri: string): PasteDataRecord-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| uri | string | 是 | URI内容，需符合标准URI格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | 一条新建的URI内容条目。 |

**示例**

```TypeScript
let record: pasteboard.PasteDataRecord = pasteboard.createUriRecord('dataability:///com.example.myapplication1/user.txt');
```

