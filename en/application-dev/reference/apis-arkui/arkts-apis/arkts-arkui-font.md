# @ohos.font(Custom Font Registration)

The **font** module provides APIs for registering custom fonts.

> **NOTE:** 
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).
> 
> - You are advised to use the [loadFontSync](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontcollection-c.md#loadfontsync) API of the font engine to register custom fonts.

**Since:** 9

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
| [getUIFontConfig](arkts-arkui-font-getuifontconfig-f.md) | Obtains the UI font configuration information in the system font configuration file. |
| [registerFont](arkts-arkui-font-registerfont-f.md) | Registers a custom font with the font manager. |

### Interfaces

| Name | Description |
| --- | --- |
| [FontInfo](arkts-arkui-font-fontinfo-i.md) | Information about the system font. |
| [FontOptions](arkts-arkui-font-fontoptions-i.md) | Information about the custom font to register. |
| [UIFontAdjustInfo](arkts-arkui-font-uifontadjustinfo-i.md) | UI font configuration of the system. |
| [UIFontAliasInfo](arkts-arkui-font-uifontaliasinfo-i.md) | UI font configuration of the system. |
| [UIFontConfig](arkts-arkui-font-uifontconfig-i.md) | UI font configuration of the system. |
| [UIFontFallbackGroupInfo](arkts-arkui-font-uifontfallbackgroupinfo-i.md) | UI font configuration of the system. |
| [UIFontFallbackInfo](arkts-arkui-font-uifontfallbackinfo-i.md) | UI font configuration of the system. |
| [UIFontGenericInfo](arkts-arkui-font-uifontgenericinfo-i.md) | UI font configuration of the system. |
