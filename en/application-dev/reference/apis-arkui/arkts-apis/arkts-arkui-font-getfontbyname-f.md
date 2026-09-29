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
> - Since API version 10, you can use the [getFont](arkts-arkui-arkui-uicontext-uicontext-c.md#getfont) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 10

**Deprecated since:** 18

**Substitutes:** getFontByName

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-font-function getFontByName(fontName: string): FontInfo--><!--Device-font-function getFontByName(fontName: string): FontInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fontName | string | Yes | System font name. |

**Return value:**

| Type | Description |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | Font details, including attributes such as the path, name, font weight, width, and whether it is italic. |
