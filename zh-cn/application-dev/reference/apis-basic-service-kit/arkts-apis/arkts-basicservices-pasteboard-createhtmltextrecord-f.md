# createHtmlTextRecord

## createHtmlTextRecord

```TypeScript
function createHtmlTextRecord(htmlText: string): PasteDataRecord
```

创建一条HTML内容的条目。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** 9

**替代接口：** [createRecord](arkts-basicservices-pasteboard-createrecord-f.md#createRecord)(mimeType: string, value: ValueType)

<!--Device-pasteboard-function createHtmlTextRecord(htmlText: string): PasteDataRecord--><!--Device-pasteboard-function createHtmlTextRecord(htmlText: string): PasteDataRecord-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| htmlText | string | 是 | HTML内容，需符合标准HTML格式。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [PasteDataRecord](arkts-basicservices-pasteboard-pastedatarecord-i.md) | 一条新建的HTML内容条目。 |

## 示例

```TypeScript
let html = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
let record: pasteboard.PasteDataRecord = pasteboard.createHtmlTextRecord(html);
```

