# Decoration

```TypeScript
interface Decoration
```

Describes a text decoration.

**Since:** 12

<!--Device-text-interface Decoration--><!--Device-text-interface Decoration-End-->

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

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-Decoration-color?: common2D.Color--><!--Device-Decoration-color?: common2D.Color-End-->

**System capability:** SystemCapability.Graphics.Drawing

## decorationStyle

```TypeScript
decorationStyle?: TextDecorationStyle
```

Style of the decoration. The default value is **SOLID**.

**Type:** [TextDecorationStyle](arkts-arkgraphics2d-text-textdecorationstyle-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-Decoration-decorationStyle?: TextDecorationStyle--><!--Device-Decoration-decorationStyle?: TextDecorationStyle-End-->

**System capability:** SystemCapability.Graphics.Drawing

## decorationThicknessScale

```TypeScript
decorationThicknessScale?: number
```

Scale factor for the thickness of the decoration line. The value is a floating point number. The default value is **1.0**. If the value is less than or equal to 0, no decoration line is drawn.

**Type:** number

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-Decoration-decorationThicknessScale?: double--><!--Device-Decoration-decorationThicknessScale?: double-End-->

**System capability:** SystemCapability.Graphics.Drawing

## textDecoration

```TypeScript
textDecoration?: TextDecorationType
```

Type of the decoration. The default value is **NONE**.

**Type:** [TextDecorationType](arkts-arkgraphics2d-text-textdecorationtype-e.md)

**Since:** 12

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 22.

<!--Device-Decoration-textDecoration?: TextDecorationType--><!--Device-Decoration-textDecoration?: TextDecorationType-End-->

**System capability:** SystemCapability.Graphics.Drawing
