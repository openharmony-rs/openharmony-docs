# createPlainTextData

## Modules to Import

```TypeScript
import { pasteboard } from '@kit.BasicServicesKit';
```

## createPlainTextData

```TypeScript
function createPlainTextData(text: string): PasteData
```

Creates a **PasteData** object of the plain text type.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [createData](arkts-basicservices-pasteboard-createdata-f.md)(mimeType: string, value: ValueType)

**System capability:** SystemCapability.MiscServices.Pasteboard

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| text | string | Yes | Plain text. |

**Return value:**

| Type | Description |
| --- | --- |
| [PasteData](arkts-basicservices-pasteboard-pastedata-i.md) | **PasteData** object. |

**Examples**

```TypeScript
let pasteData: pasteboard.PasteData = pasteboard.createPlainTextData('content');
```
