# WithThemeOptions

Defines the default theme and color mode for components within the **WithTheme** scope.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## colorMode

```TypeScript
colorMode?: ThemeColorMode
```

Color mode for components in the **WithTheme** scope.

Default value: **ThemeColorMode.SYSTEM**

**Type:** [ThemeColorMode](arkts-arkui-themecolormode-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## theme

```TypeScript
theme?: CustomTheme
```

Default theme for components in the **WithTheme** scope.

Default value: **undefined**. The default style follows the [default token style](../../../ui/theme_skinning.md#system-default-token-color-values).

**Type:** [CustomTheme](arkts-arkui-customtheme-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
