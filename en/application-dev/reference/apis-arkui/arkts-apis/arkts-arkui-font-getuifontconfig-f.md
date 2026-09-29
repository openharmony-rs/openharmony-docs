# getUIFontConfig

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## getUIFontConfig

```TypeScript
function getUIFontConfig(): UIFontConfig
```

Obtains the UI font configuration in the system font configuration file. This API is commonly used in scenarios where the system font configuration needs to be analyzed or viewed, such as font management tools, font debugging and diagnosis, and font configuration information display.

This API only supports obtaining the information in the configuration file, and **undefined** may be returned when the UI context is not clear. To obtain the full font configuration information, it is recommended to use the [getSystemFontFullNamesByType](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-getsystemfontfullnamesbytype-f.md) API of the font engine to obtain the latest font list data supported by the system.

> **NOTE:** 
> 
> You need to first obtain the [Font](arkts-arkui-arkui-uicontext-uicontext-c.md) object through the
> [getFont](arkts-arkui-arkui-uicontext-uicontext-c.md#getfont) API in [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md), and
> then call the related API through the object. Directly using **getUIFontConfig** may cause the issue of
> [ambiguous UI context](../../../ui/arkts-global-interface.md#ambiguous-ui-context).

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-font-function getUIFontConfig(): UIFontConfig--><!--Device-font-function getUIFontConfig(): UIFontConfig-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | UI font configuration of the system, including the font directory, generic font group, and fallback font group. |
