# @ohos.font(Custom Font Registration)

This module provides capabilities such as registering custom fonts and obtaining the system font list, font details, and system font configuration. It is applicable to scenarios where applications need to use custom font styles (such as brand and icon fonts) or obtain system font information. By using this module, you can unify brand fonts, improve the aesthetics and consistency of the user interface, and meet diverse design requirements.

> **NOTE:** 
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).
> 
> - You are advised to use the [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) API of the font engine to register custom fonts.

**Since:** 9

<!--Device-unnamed-declare namespace font--><!--Device-unnamed-declare namespace font-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { font } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getFontByName](arkts-arkui-font-getfontbyname-f.md) | Obtains information about a system font based on the font name. |
| [getSystemFontList](arkts-arkui-font-getsystemfontlist-f.md) | Obtains this system font list. |
| [getUIFontConfig](arkts-arkui-font-getuifontconfig-f.md) | Obtains the UI font configuration in the system font configuration file. This API is commonly used in scenarios where the system font configuration needs to be analyzed or viewed, such as font management tools, font debugging and diagnosis, and font configuration information display. |
| [registerFont](arkts-arkui-font-registerfont-f.md) | Registers a custom font with the font manager. |

### Interfaces

| Name | Description |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | Information about the system font. |
| [FontOptions](arkts-arkui-font-fontoptions-i.md) | Information about the custom font to register. |
| [UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md) | Provides a mapping list between the original weight value of a font and the actual displayed weight value. |
| [UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md) | Defines font alias configuration information. |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | UI font configuration of the system. |
| [UIFontFallbackGroupInfo](arkts-arkui-font-uifontfallbackgroupinfo-i.md) | Defines a list of fallback generic font families. |
| [UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md) | Provides the fallback font of the font set. |
| [UIFontGenericInfo](arkts-arkui-font-uifontgenericinfo-i.md) | Defines a list of supported generic font families. |
