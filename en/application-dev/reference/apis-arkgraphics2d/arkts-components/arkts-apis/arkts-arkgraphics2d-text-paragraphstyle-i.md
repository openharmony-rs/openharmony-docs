# ParagraphStyle

```TypeScript
interface ParagraphStyle
```

Represents a paragraph style, which controls the overall layout behavior of a paragraph, including attributes such as alignment, line break strategy, and maximum number of lines. ParagraphStyle serves as a required parameter of the [ParagraphBuilder](arkts-arkgraphics2d-text-paragraphbuilder-c.md) constructor, and works together with [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md) (which controls text-level styles) to determine the final typesetting result of the paragraph.

**Since:** 12

**System capability:** SystemCapability.Graphics.Drawing

## Modules to Import

```TypeScript
import { text } from '@kit.ArkGraphics2D';
```

## align

```TypeScript
align?: TextAlign
```

Text alignment mode. The default value is **START**. This parameter is invalid when the **tab** parameter is configured.

**Type:** [TextAlign](arkts-arkgraphics2d-text-textalign-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## autoSpace

```TypeScript
autoSpace?: boolean
```

Sets whether to enable automatic spacing during text typography. **true** indicates that the automatic spacing feature is enabled. In this case, automatic spacing applies between CJK (Chinese, Japanese, and Korean) and Western characters (Latin, Cyrillic, and Greek), between CJK and digits, between CJK and copyright symbols, between copyright symbols and digits, and between copyright symbols and Western characters. **false** (default) indicates that the automatic spacing feature is disabled.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## breakStrategy

```TypeScript
breakStrategy?: BreakStrategy
```

Text break strategy. The default value is **GREEDY**.

**Type:** [BreakStrategy](arkts-arkgraphics2d-text-breakstrategy-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## compressHeadPunctuation

```TypeScript
compressHeadPunctuation?: boolean
```

Sets whether to use punctuation compression at the beginning of a line in text layout. **true** means yes; **false** otherwise. The default value is **false**.

**NOTE:** 

1. The font file must support the ss08 feature in [FontFeature](arkts-arkgraphics2d-text-fontfeature-i.md).
Otherwise, compression cannot be performed.
2. Only the punctuations within the punctuation compression range at the beginning of a line
are in the scope of this feature.

Punctuation range at the beginning of a line.

| Punctuation| Unicode Code Point| Unicode Name|  
|---------|---------|-------------|  
| 「| U+300C | LEFT CORNER BRACKET |
| 『| U+300E | LEFT WHITE CORNER BRACKET |
| " | U+201C | LEFT DOUBLE QUOTATION MARK |
| ' | U+2018 | LEFT SINGLE QUOTATION MARK |
| （| U+FF08 | FULLWIDTH LEFT PARENTHESIS |
| 《| U+300A | LEFT DOUBLE ANGLE BRACKET |
| 〈| U+3008 | LEFT ANGLE BRACKET |
| 【| U+3010 | LEFT BLACK LENTICULAR BRACKET |
| 〖| U+3016 | LEFT WHITE LENTICULAR BRACKET |
| 〔| U+3014 | LEFT TORTOISE SHELL BRACKET |
| ［| U+FF3B | FULLWIDTH LEFT SQUARE BRACKET |
| ｛| U+FF5B | FULLWIDTH LEFT CURLY BRACKET |

**Type:** boolean

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## fallbackLineSpacing

```TypeScript
fallbackLineSpacing?: boolean
```

Sets whether to enable line height rollback during text layout. If the set line height is less than the actual line height, the line height is rolled back to the actual line height. **true** means yes; **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## firstLineHeadIndent

```TypeScript
firstLineHeadIndent?: number
```

First line indent of the paragraph. The indent value must be greater than or equal to 0, in physical pixels (px). The default value is **0**.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## headIndents

```TypeScript
headIndents?: Array<number>
```

Array of head indents. Each element in the array represents the indent value of one line. When the actual number of text lines exceeds the number of elements in the indent array, the indent of the excess lines is the last value in the array. All indent values must be greater than or equal to 0, in physical pixels (px). The default value is an empty array.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## includeFontPadding

```TypeScript
includeFontPadding?: boolean
```

Sets whether to use padding at the beginning and end of a line in text layout. **true** means yes; **false** otherwise. The default value is **false**.

**Type:** boolean

**Since:** 23

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.Graphics.Drawing

## lineSpacing

```TypeScript
lineSpacing?: number
```

Line spacing, in physical pixels (px). The default value is **0**. lineSpacing is not restricted by lineHeightMaximum and lineHeightMinimum in [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md). The last line retains line spacing by default. You can disable line spacing for the last line by setting [ParagraphStyle](arkts-arkgraphics2d-text-paragraphstyle-i.md)'s textHeightBehavior to DISABLE_ALL or DISABLE_LAST_ASCENT.

**Type:** number

**Since:** 21

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines. The value is an integer. The default value is **1e9**.

**Type:** number

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## orphanCharOptimization

```TypeScript
orphanCharOptimization?: boolean
```

Whether to enable orphan character optimization during text typesetting. Orphan character optimization improves text layout by handling isolated characters (the first character of the last line of a paragraph) more efficiently. When enabled, it adjusts line break points to avoid isolated characters as much as possible. The orphan character optimization feature takes effect only when [wordBreak](arkts-arkgraphics2d-text-wordbreak-e.md) is not BREAK_ALL and the locale of the first [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md) of the text to be typeset is "zh-Hans" or "zh-Hant". The value **true** enables orphan character optimization, and **false** disables it. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## punctuationOverflow

```TypeScript
punctuationOverflow?: boolean
```

Whether to enable end-of-line punctuation hanging during text typesetting. The value **true** enables end-of-line punctuation hanging, allowing a single punctuation mark at the end of a line to exceed the typesetting width without wrapping. The value **false** disables end-of-line punctuation hanging. The default value is **false**.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## strutStyle

```TypeScript
strutStyle?: StrutStyle
```

Strut style. The default value is the initial **StrutStyle** object.

**Type:** [StrutStyle](arkts-arkgraphics2d-text-strutstyle-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## tab

```TypeScript
tab?: TextTab
```

Alignment mode and position of the text after the tab character in a paragraph. By default, the tab character is replaced with a space. This parameter is invalid when it is used together with the **align** parameter or the **ellipsis** parameter in [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md).

**Type:** [TextTab](arkts-arkgraphics2d-text-texttab-i.md)

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## tailIndents

```TypeScript
tailIndents?: Array<number>
```

Array of tail indents. Each element in the array represents the indent value of one line. When the actual number of text lines exceeds the number of elements in the indent array, the indent of the excess lines is the last value in the array. All indent values must be greater than or equal to 0, in physical pixels (px). The default value is an empty array.

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Graphics.Drawing

## textDirection

```TypeScript
textDirection?: TextDirection
```

Text direction. The default value is **LTR**.

**Type:** [TextDirection](arkts-arkgraphics2d-text-textdirection-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## textHeightBehavior

```TypeScript
textHeightBehavior?: TextHeightBehavior
```

Text height modifier pattern. The default value is **ALL**.

**Type:** [TextHeightBehavior](arkts-arkgraphics2d-text-textheightbehavior-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## textStyle

```TypeScript
textStyle?: TextStyle
```

Text style applied to the paragraph. The default value is the initial text style.

**Type:** [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## trailingSpaceOptimized

```TypeScript
trailingSpaceOptimized?: boolean
```

Whether to consider the alignment impact of trailing spaces during text layout. The value **true** indicates that the alignment impact of trailing spaces is ignored, and the value **false** indicates that the alignment impact of trailing spaces is considered. The default value is **false**.

**Type:** boolean

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## verticalAlign

```TypeScript
verticalAlign?: TextVerticalAlign
```

Text vertical alignment mode. The default value is BASELINE, which means text baseline alignment. This attribute takes effect when line height scaling is enabled (that is, when [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)'s heightScaleis set) or when text in different font sizes is mixed in a line (that is, when [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)'s fontSize is set). If there is superscript or subscript text in the line (that is, text with [TextStyle](arkts-arkgraphics2d-text-textstyle-i.md)'s badgeType attribute set), the superscript or subscripttext participates in vertical alignment in the same way as normal text.

**Type:** [TextVerticalAlign](arkts-arkgraphics2d-text-textverticalalign-e.md)

**Since:** 20

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

Word break type. The default value is **BREAK_WORD**.

**Type:** [WordBreak](arkts-arkgraphics2d-text-wordbreak-e.md)

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.Graphics.Drawing
