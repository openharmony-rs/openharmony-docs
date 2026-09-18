# getFontByName

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## getFontByName

```TypeScript
function getFontByName(fontName: string): FontInfo
```

Obtains information about a system font based on the font name.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getFont](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** getFontByName

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontName | string | Yes | System font name. |

**Return value:**

| Type | Description |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | Information about the system font. |
