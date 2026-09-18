# TextTab

Implements a paragraph-style text tab, which stores the alignment mode and position.

**Since:** 18

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## alignment

```TypeScript
alignment: TextAlign
```

Text alignment method after the tab character in a paragraph. It supports the LEFT (left alignment), RIGHT (right alignment), and CENTER (center alignment) alignment methods of [TextAlign](arkts-arkgraphics2d-text-textalign-e.md). Unlisted enum values are treated as left alignment, with left alignment as the default.

**Type:** [TextAlign](arkts-arkgraphics2d-text-textalign-e.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## location

```TypeScript
location: number
```

Alignment position of the text following the tab character. The value is a floating point number, in px. The minimum value is 1.0. When the value is less than 1.0, the tab character is replaced with a space.

**Type:** number

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
