# WithThemeOptions

```TypeScript
declare interface WithThemeOptions
```

Sets the theme colors and dark/light mode for components within the **WithTheme** scope.

**Since:** 12

<!--Device-unnamed-declare interface WithThemeOptions--><!--Device-unnamed-declare interface WithThemeOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

Used to specify the dark/light mode of the component colors within the scope of WithTheme. Value rules: **ThemeColorMode.SYSTEM** follows the system dark/light mode settings, **ThemeColorMode.DARK** forces the dark mode, and **ThemeColorMode.LIGHT** forces the light mode. When setting the dark/light mode, a dark.json resource file must be added for the setting to take effect.

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

Used to set the custom theme colors of components within the scope of WithTheme.

Default value: **undefined**, which means the default colors follow the system [token default styles](../../../ui/theme_skinning.md#system-default-token-color-values).

**Type:** [CustomTheme](arkts-arkui-withtheme-comp-customtheme-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WithThemeOptions-theme?: CustomTheme--><!--Device-WithThemeOptions-theme?: CustomTheme-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
