# ThemeControl

Class ThemeControl provides the Theme management for whole Ability and pages.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Colors, CustomColors, Theme, ThemeControl, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## setDefaultTheme

```TypeScript
static setDefaultTheme(theme: CustomTheme): void
```

Sets the default Theme:

- for whole Ability when invoked from the Ability level code.  
- for the ArkUI page and for later opened pages when invoked at the ArkUI page level.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| theme | [CustomTheme](arkts-arkui-arkui-theme-customtheme-i.md) | Yes |  |
