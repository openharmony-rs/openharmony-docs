# WithThemeOptions

```TypeScript
declare interface WithThemeOptions
```

Defines the default theme and color mode for components within the **WithTheme** scope.

**Since:** 12

<!--Device-unnamed-declare interface WithThemeOptions--><!--Device-unnamed-declare interface WithThemeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

Color mode for components in the **WithTheme** scope.

Default value: **ThemeColorMode.SYSTEM**

**Type:** [ThemeColorMode](arkts-arkui-common-comp-themecolormode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WithThemeOptions-colorMode?: ThemeColorMode--><!--Device-WithThemeOptions-colorMode?: ThemeColorMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: CustomTheme
```

Default theme for components in the **WithTheme** scope.

Default value: **undefined**. The default style follows the [default token style](../../../ui/theme_skinning.md#system-default-token-color-values).

**Type:** [CustomTheme](arkts-arkui-withtheme-comp-customtheme-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WithThemeOptions-theme?: CustomTheme--><!--Device-WithThemeOptions-theme?: CustomTheme-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
