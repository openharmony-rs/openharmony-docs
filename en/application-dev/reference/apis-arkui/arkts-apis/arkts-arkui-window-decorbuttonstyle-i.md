# DecorButtonStyle

```TypeScript
interface DecorButtonStyle
```

Describes the button style of the system decoration bar.

**Since:** 14

<!--Device-window-interface DecorButtonStyle--><!--Device-window-interface DecorButtonStyle-End-->

**System capability:** SystemCapability.Window.SessionManager

## Modules to Import

```TypeScript
import { window } from '@kit.ArkUI';
```

## buttonBackgroundCornerRadius

```TypeScript
buttonBackgroundCornerRadius? : number
```

Radius of the button background rounded corner. The value ranges from 4 vp to 8 vp. The default value is 4 vp.

**Type:** number

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-DecorButtonStyle-buttonBackgroundCornerRadius? : int--><!--Device-DecorButtonStyle-buttonBackgroundCornerRadius? : int-End-->

**System capability:** SystemCapability.Window.SessionManager

## buttonBackgroundSize

```TypeScript
buttonBackgroundSize? : number
```

Size of the button when it is highlighted. The value ranges from 20 vp to 40 vp. The default value is 28 vp.

**Type:** number

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-DecorButtonStyle-buttonBackgroundSize? : int--><!--Device-DecorButtonStyle-buttonBackgroundSize? : int-End-->

**System capability:** SystemCapability.Window.SessionManager

## buttonIconSize

```TypeScript
buttonIconSize? : number
```

Size of the button icon. The value ranges from 16 vp to 24 vp. The default value is 20 vp.

**Type:** number

**Since:** 20

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 20.

<!--Device-DecorButtonStyle-buttonIconSize? : int--><!--Device-DecorButtonStyle-buttonIconSize? : int-End-->

**System capability:** SystemCapability.Window.SessionManager

## closeButtonRightMargin

```TypeScript
closeButtonRightMargin? : number
```

Margin between the rightmost edge of the close button and the window. The value ranges from 6 vp to 22 vp. The default value is 20 vp.

**Type:** number

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-DecorButtonStyle-closeButtonRightMargin? : int--><!--Device-DecorButtonStyle-closeButtonRightMargin? : int-End-->

**System capability:** SystemCapability.Window.SessionManager

## colorMode

```TypeScript
colorMode?: ConfigurationConstant.ColorMode
```

Color mode. Buttons automatically adapt to light colors in dark mode and to dark colors in light mode. If this parameter is not set, they will automatically match the system color mode.

**Type:** [ConfigurationConstant.ColorMode](../../apis-ability-kit/arkts-apis/arkts-ability-configurationconstant-colormode-e.md)

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-DecorButtonStyle-colorMode?: ConfigurationConstant.ColorMode--><!--Device-DecorButtonStyle-colorMode?: ConfigurationConstant.ColorMode-End-->

**System capability:** SystemCapability.Window.SessionManager

## spacingBetweenButtons

```TypeScript
spacingBetweenButtons? : number
```

Spacing between buttons. The value ranges from 8 vp to 24 vp. The default value is 12 vp.

**Type:** number

**Since:** 14

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 14.

<!--Device-DecorButtonStyle-spacingBetweenButtons? : int--><!--Device-DecorButtonStyle-spacingBetweenButtons? : int-End-->

**System capability:** SystemCapability.Window.SessionManager
