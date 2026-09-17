# createHtmlData

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## createHtmlData

```TypeScript
function createHtmlData(htmlText: string): PasteData
```

Creates a **PasteData** object of the HTML type.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [createData](arkts-basicservices-pasteboard-createdata-f.md)(mimeType: string, value: ValueType)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| htmlText | string | Yes | HTML content. |

**Return value:**

| Type | Description |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | **PasteData** object. |

**Examples**

```TypeScript
let html = "<!DOCTYPE html>\n" + "<html>\n" + "<head>\n" + "<meta charset=\"utf-8\">\n" + "<title>HTML-PASTEBOARD_HTML</title>\n" + "</head>\n" + "<body>\n" + "    <h1>HEAD</h1>\n" + "    <p></p>\n" + "</body>\n" + "</html>";
let pasteData: pasteboard.PasteData = pasteboard.createHtmlData(html);
```
