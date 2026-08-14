# createPlainTextRecord

## createPlainTextRecord

```TypeScript
function createPlainTextRecord(text: string): PasteDataRecord
```

创建一条纯文本内容条目。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [createRecord](arkts-basicservices-pasteboard-createrecord-f.md#createRecord)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createPlainTextRecord(text: string): PasteDataRecord--><!--Device-pasteboard-function createPlainTextRecord(text: string): PasteDataRecord-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| text | string | 是 | 纯文本内容。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | 一条新建的纯文本内容条目。 |

## 示例

```TypeScript
let record: pasteboard.PasteDataRecord = pasteboard.createPlainTextRecord('hello');
```

