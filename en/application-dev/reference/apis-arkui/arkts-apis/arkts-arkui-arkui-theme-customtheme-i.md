# CustomTheme

```TypeScript
export declare interface CustomTheme
```

Defines a custom theme object.

**Since:** 12

<!--Device-unnamed-export declare interface CustomTheme--><!--Device-unnamed-export declare interface CustomTheme-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { Colors, CustomColors, Theme, ThemeControl, CustomTheme, CustomDarkColors } from '@kit.ArkUI';
```

## colors

```TypeScript
colors?: CustomColors
```

Custom light theme color resources.

**Type:** [CustomColors](arkts-arkui-customcolors-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-CustomTheme-colors?: CustomColors--><!--Device-CustomTheme-colors?: CustomColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## darkColors

```TypeScript
darkColors?: CustomDarkColors
```

Custom dark theme color resources.

Note: If **darkColors** is not set, the **colors** configuration in light color mode is used and does not change with the system's dark/light color mode. If the corresponding color is set using the resources in the **dark** directory, the resources in the **dark** directory are preferentially used.

**Type:** [CustomDarkColors](arkts-arkui-customdarkcolors-t.md)

**Default:** If not set darkColors, color value will same as colors under light mode and will not change with color mode, unless the color is setted by resource in dark directory.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-CustomTheme-darkColors?: CustomDarkColors--><!--Device-CustomTheme-darkColors?: CustomDarkColors-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
