# setTextHighContrast

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## setTextHighContrast

```TypeScript
function setTextHighContrast(action : TextHighContrast): void
```

Sets the high contrast mode for text rendering.

The setting of this API takes effect for the entire process, and all pages in the process share the same mode.

You can call this API to set the high contrast mode, or enable or disable the high contrast mode by toggling the switch on the system settings screen. This API is used to set the high contrast mode for text rendering. The setting of this API takes precedence over the one based on system settings.

This API does not take effect for text drawn by the app through APIs such as Canvas. It only takes effect for text rendered using system text components.

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| action | [TextHighContrast](arkts-arkgraphics2d-text-texthighcontrast-e.md) | Yes | High contrast mode for text rendering. |

**Examples**

```TypeScript
text.setTextHighContrast(text.TextHighContrast.TEXT_APP_DISABLE_HIGH_CONTRAST)
```
