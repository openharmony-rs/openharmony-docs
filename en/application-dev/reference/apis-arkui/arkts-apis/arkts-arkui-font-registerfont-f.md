# registerFont

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## registerFont

```TypeScript
function registerFont(options: FontOptions): void
```

Registers a custom font with the font manager.

This API is asynchronous and does not support concurrent calls.

> **NOTE:** 
> 
> - Since API version 10, you can use the [getFont](../../../reference/apis-arkui/arkts-apis-uicontext-uicontext.md#getfont) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md) to obtain the [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object associated with the current UI context.

**Since:** 9

**Deprecated since:** 18

**Substitutes:** registerFont

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FontOptions](arkts-arkui-font-fontoptions-i.md) | Yes | Information about the custom font to register. |
