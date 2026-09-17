# TextShadow

Represents a text shadow.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## blurRadius

```TypeScript
blurRadius?: number
```

Blur radius, a floating-point value in physical pixels (px), with a default value of **0.0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## color

```TypeScript
color?: common2D.Color
```

Color of the text shadow. The default value is black Color(255, 0, 0, 0).

**Type:** [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## point

```TypeScript
point?: common2D.Point
```

Offset position of the text shadow relative to the current text. The horizontal and vertical coordinates must be greater than or equal to 0, in physical pixels (px). The default value is common2D.Point(0, 0).

**Type:** [common2D.Point](arkts-arkgraphics2d-common2d-point-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
