# FontMetrics

Describes the attributes that describe the font size and layout. A typeface has similar font metrics.

**Since:** 11

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { drawing } from '@kit.ArkGraphics2D';
```

## ascent

```TypeScript
ascent: number
```

Distance from the baseline to the highest coordinate of the text. The value is a floating point number.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## avgCharWidth

```TypeScript
avgCharWidth?: number
```

Average character width.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## bottom

```TypeScript
bottom: number
```

Maximum distance from the baseline to the lowest coordinate of the text. The value is a floating point number.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## capHeight

```TypeScript
capHeight?: number
```

Height of a capital letter. The value is usually a negative value.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## descent

```TypeScript
descent: number
```

Distance from the baseline to the lowest coordinate of the text. The value is a floating point number.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## flags

```TypeScript
flags?: FontMetricsFlags
```

Font measurement flags that are valid.

**Type:** [FontMetricsFlags](arkts-arkgraphics2d-drawing-fontmetricsflags-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## leading

```TypeScript
leading: number
```

Interline spacing, that is, the distance from the descent of one line of text to the ascent of the next line. The value is a floating point number.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## maxCharWidth

```TypeScript
maxCharWidth?: number
```

Maximum character width.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## strikethroughPosition

```TypeScript
strikethroughPosition?: number
```

Vertical distance from the baseline to the bottom of the strikethrough. The value is usually a negative value.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## strikethroughThickness

```TypeScript
strikethroughThickness?: number
```

Thickness of the strikethrough.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## top

```TypeScript
top: number
```

Maximum distance from the baseline to the highest coordinate of the text. The value is a floating point number.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## underlinePosition

```TypeScript
underlinePosition?: number
```

Vertical distance from the baseline to the top of the underline. The value is usually a positive number.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## underlineThickness

```TypeScript
underlineThickness?: number
```

Thickness of the underline.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## xHeight

```TypeScript
xHeight?: number
```

Height of the lowercase letter x. The value is usually a negative value.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## xMax

```TypeScript
xMax?: number
```

Horizontal distance from the rightmost edge of any glyph bounding box to the origin. The value is a positive number, indicating the maximum horizontal coordinate across all glyph bounding boxes.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## xMin

```TypeScript
xMin?: number
```

Horizontal distance from the leftmost edge of any glyph bounding box to the origin. This value is usually less than 0, indicating the minimum horizontal coordinate across all glyph bounding boxes.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
