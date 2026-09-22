# TextStyle

```TypeScript
interface TextStyle
```

Represents a text style, which controls the visual appearance attributes of text, including font, color, font size, spacing, decoration lines, and shadows. TextStyle is applied to subsequently added text content through the [pushStyle](arkts-arkgraphics2d-text-paragraphbuilder-c.md#pushstyle) method of [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md), and works together with [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md) (which controls paragraph-level attributes). Within the same paragraph, you can call pushStyle multiple times to apply different styles to different text segments.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## backgroundRect

```TypeScript
backgroundRect?: RectStyle
```

Text rectangle style. Pass this parameter when you need to add a background rectangle to text (such as setting the background color, rounded corners, etc.).

**Type:** [RectStyle](arkts-arkgraphics2d-text-rectstyle-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## badgeType

```TypeScript
badgeType?: TextBadgeType
```

Sets whether to use superscript or subscript in text layout. **TEXT_SUPERSCRIPT** indicates that superscript is enabled, and **TEXT_SUBSCRIPT** indicates that subscript is enabled. The default value is **TEXT_BADGE_NONE**, indicating that neither superscript nor subscript is enabled.

**Type:** [TextBadgeType](arkts-arkgraphics2d-text-textbadgetype-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## baseline

```TypeScript
baseline?: TextBaseline
```

Text baseline type. The default value is **ALPHABETIC**.

**Type:** [TextBaseline](arkts-arkgraphics2d-text-textbaseline-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## baselineShift

```TypeScript
baselineShift?: number
```

Vertical offset distance of the text baseline, in physical pixels (px). The default value is **0.0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## color

```TypeScript
color?: common2D.Color
```

Text color. The default color is white.

**Type:** [common2D.Color](arkts-arkgraphics2d-common2d-color-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## decoration

```TypeScript
decoration?: Decoration
```

Text decoration. By default, no decoration is used.

**Type:** [Decoration](arkts-arkgraphics2d-text-decoration-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## ellipsis

```TypeScript
ellipsis?: string
```

Ellipsis text. When the ellipsis takes effect, this field value replaces the ellipsis portion. The default value is an empty string, which uses the system default ellipsis … (U+2026). When configured together with the tab attribute of ParagraphStyle, the tab attribute does not take effect.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## ellipsisMode

```TypeScript
ellipsisMode?: EllipsisMode
```

Ellipsis type. The default value is **END**, indicating that the ellipsis is at the end of a line.

**Type:** [EllipsisMode](arkts-arkgraphics2d-text-ellipsismode-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontEdging

```TypeScript
fontEdging?: drawing.FontEdging
```

Edge processing mode for drawing texts. The default value is **ANTI_ALIAS**.

**Type:** [drawing.FontEdging](arkts-arkgraphics2d-drawing-fontedging-e.md)

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.Graphics.Drawing

## fontFamilies

```TypeScript
fontFamilies?: Array<string>
```

List of font family names. The default value is empty, which matches the system font. When using a custom font, specify the name used when loading the font in this list. When set together with fontTypefaces, fontTypefaces takes precedence and fontFamilies does not take effect.

**Type:** Array&lt;string&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontFeatures

```TypeScript
fontFeatures?: Array<FontFeature>
```

Array of text font features. Pass this parameter when you need to enable or disable specific font features (such as ligatures, kerning adjustment, etc.).

**Type:** Array&lt;[FontFeature](arkts-arkgraphics2d-text-fontfeature-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontSize

```TypeScript
fontSize?: number
```

Font size, a floating-point value with a default value of **14.0**, measured in physical pixels (px).

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

Font style. The default value is **NORMAL**.

**Type:** [FontStyle](arkts-arkgraphics2d-text-fontstyle-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontTypefaces

```TypeScript
fontTypefaces?: Array<drawing.Typeface>
```

Array of specified typesetting font objects, used to prioritize the specified font objects for text shaping and skip the font matching process. When a font object in the array cannot shape some characters, the unshaped characters will be shaped using the system font. The default value is an empty array, indicating that no font object is specified and the default font matching process is used.

When fontTypefaces is set together with [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).fontFamilies, fontTypefaces takes precedence.

**Type:** Array&lt;[drawing.Typeface](arkts-arkgraphics2d-drawing-typeface-c.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## fontVariations

```TypeScript
fontVariations?: Array<FontVariation>
```

Array of variable font properties. Pass this parameter when you need to adjust the variable axis parameters of a variable font (such as the font weight axis, font width axis, etc.).

**Type:** Array&lt;[FontVariation](arkts-arkgraphics2d-text-fontvariation-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontWeight

```TypeScript
fontWeight?: FontWeight
```

Font weight. The default value is W400. Before &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, only variable fonts in system fonts support font weight adjustment. Since &lt;!--RP1--&gt;OpenHarmony 6.1&lt;!--RP1End--&gt;, variable fonts in both system fonts and third-party registered fonts support font weight adjustment. For non-variable fonts, setting a font weight value less than semi-bold (W600) results in no change in font thickness, while setting a font weight value greater than or equal to semi-bold (W600) may trigger a pseudo-bold effect.

**Type:** [FontWeight](arkts-arkgraphics2d-text-fontweight-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## fontWidth

```TypeScript
fontWidth?: FontWidth
```

Font width. The default value is **NORMAL**.

**Type:** [FontWidth](arkts-arkgraphics2d-text-fontwidth-e.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## halfLeading

```TypeScript
halfLeading?: boolean
```

Whether half leading is enabled. Half leading is the leading split in half and applied equally to the top and bottom edges. The value **true** means that half leading is enabled, and **false** means the opposite. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## heightOnly

```TypeScript
heightOnly?: boolean
```

The value **true** means the text box height is set based on the font size and heightScale, and **false** means the text box height is set based on the line height and line spacing. The default value is **false**.

**Type:** boolean

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## heightScale

```TypeScript
heightScale?: number
```

Scale factor of the line height. The value is a floating point number. The default value is **1.0**. This parameter is valid only when **heightOnly** is set to** true**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## letterSpacing

```TypeScript
letterSpacing?: number
```

Character spacing, a floating-point value in physical pixels (px) with a default value of **0.0**. A positive value widens the character gap, while a negative value narrows it.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## lineHeightMaximum

```TypeScript
lineHeightMaximum?: number
```

Maximum line height, in physical pixels (px). If the line height is scaled, the maximum line height takes effect when [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).heightScale is greater than 0. The value is a positive floating point number. The default value is **Number.MAX_VALUE**.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## lineHeightMinimum

```TypeScript
lineHeightMinimum?: number
```

Minimum line height, in physical pixels (px). If the line height is scaled, the minimum line height takes effect when [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).heightScale is greater than 0. The value is a non-negative floating point number. The default value is **0**.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## lineHeightStyle

```TypeScript
lineHeightStyle?: LineHeightStyle
```

Scaling base style of the line height. The default value is **FONT_SIZE**.

**Type:** [LineHeightStyle](arkts-arkgraphics2d-text-lineheightstyle-e.md)

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## locale

```TypeScript
locale?: string
```

Language type. For example, **'en-Latn'** indicates English (Latin script), **'zh-Hans'** indicates Simplified Chinese, and **'zh-Hant'** indicates Traditional Chinese. Supports two-segment language tags in the language- script format, where language complies with the ISO 639-1 standard and script complies with the ISO 15924 standard. If the locale is not specified, set to an empty string, or set to **undefined**, the default locale is **'zh-Hans'**.

**Type:** string

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## textShadows

```TypeScript
textShadows?: Array<TextShadow>
```

Array of text shadows. Pass this parameter when you need to add shadow effects to text.

**Type:** Array&lt;[TextShadow](arkts-arkgraphics2d-text-textshadow-i.md)&gt;

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## wordSpacing

```TypeScript
wordSpacing?: number
```

Word spacing, a floating-point value in physical pixels (px) with a default value of **0.0**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
