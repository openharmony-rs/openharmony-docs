# Decoration

Describes a text decoration.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## color

```TypeScript
color?: common2D.Color
```

Color of the decoration. The default value is the text color.

**Type:** [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## decorationStyle

```TypeScript
decorationStyle?: TextDecorationStyle
```

Style of the decoration. The default value is **SOLID**.

**Type:** [TextDecorationStyle](arkts-arkgraphics2d-text-textdecorationstyle-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## decorationThicknessScale

```TypeScript
decorationThicknessScale?: number
```

Scale factor for the thickness of the decoration line. The value is a floating point number. The default value is **1.0**. If the value is less than or equal to 0, no decoration line is drawn.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## textDecoration

```TypeScript
textDecoration?: TextDecorationType
```

Type of the decoration. The default value is **NONE**.

**Type:** [TextDecorationType](arkts-arkgraphics2d-text-textdecorationtype-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
