# RectStyle

```TypeScript
interface RectStyle
```

Describes the style of a rectangle.

**Since:** 12

<!--Device-text-interface RectStyle--><!--Device-text-interface RectStyle-End-->

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## borderColor

```TypeScript
borderColor?: common2D.Color
```

Rectangle border color. Default value: The default value is white.

**Type:** [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md)

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RectStyle-borderColor?: common2D.Color--><!--Device-RectStyle-borderColor?: common2D.Color-End-->

**System capability:** SystemCapability.Graphics.Drawing

## borderWidth

```TypeScript
borderWidth?: number
```

Rectangle border width. Unit: Pixel. Default value: The default value is 0.

**Type:** number

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-RectStyle-borderWidth?: double--><!--Device-RectStyle-borderWidth?: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

## color

```TypeScript
color: common2D.Color
```

Color of the rectangle.

**Type:** [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-RectStyle-color: common2D.Color--><!--Device-RectStyle-color: common2D.Color-End-->

**System capability:** SystemCapability.Graphics.Drawing

## leftBottomRadius

```TypeScript
leftBottomRadius: number
```

Lower left radius of the rectangle, in physical pixels (px).

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-RectStyle-leftBottomRadius: double--><!--Device-RectStyle-leftBottomRadius: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

## leftTopRadius

```TypeScript
leftTopRadius: number
```

Upper left radius of the rectangle, in physical pixels (px).

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-RectStyle-leftTopRadius: double--><!--Device-RectStyle-leftTopRadius: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

## rightBottomRadius

```TypeScript
rightBottomRadius: number
```

Lower right radius of the rectangle, in physical pixels (px).

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-RectStyle-rightBottomRadius: double--><!--Device-RectStyle-rightBottomRadius: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

## rightTopRadius

```TypeScript
rightTopRadius: number
```

Upper right radius of the rectangle, in physical pixels (px).

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-RectStyle-rightTopRadius: double--><!--Device-RectStyle-rightTopRadius: double-End-->

**System capability:** SystemCapability.Graphics.Drawing
