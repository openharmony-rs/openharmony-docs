# ThemeControl

```TypeScript
export declare class ThemeControl
```

Implements a **ThemeControl** object to apply the custom theme to the components in the application.

**Since:** 12

<!--Device-unnamed-export declare class ThemeControl--><!--Device-unnamed-export declare class ThemeControl-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Colors, CustomColors, Theme, ThemeControl, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## setDefaultTheme

```TypeScript
static setDefaultTheme(theme: CustomTheme): void
```

Sets a custom theme as the default, application-level theme, applying it to all components within the application. When using this API within a page, ensure that the API is called before the page's **build** API executes. When using this API within a UIAbility, ensure that the API is called in the callback after windowStage. [loadContent](arkts-arkui-window-windowstage-i.md#loadcontent1) during the **onWindowStageCreate** lifecycle phase. For a complete implementation example, see [Setting Custom Theme Colors for Application Components](../../../ui/theme_skinning.md#setting-custom-theme-colors-for-application-components).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ThemeControl-static setDefaultTheme(theme: CustomTheme): void--><!--Device-ThemeControl-static setDefaultTheme(theme: CustomTheme): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| theme | [CustomTheme](arkts-arkui-arkui-theme-customtheme-i.md) | Yes | Defines a custom theme object. |
