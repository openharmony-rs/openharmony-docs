# ParagraphStyle

```TypeScript
declare class ParagraphStyle
```

Describes the text paragraph style.

Except the first paragraph, all paragraphs are formed using the escape character '\n'.

The style of a paragraph is the one (if any) set for the first element or the paragraph style of the bound component.

Before API version 26.0.0, if the first placeholder in a styled string paragraph is [CustomSpan](arkts-arkui-customspan-c.md) or [ImageAttachment](arkts-arkui-imageattachment-c.md), the paragraph style set on that paragraph does not take effect. Since API version 26.0.0, the paragraph style takes effect.

**Since:** 12

<!--Device-unnamed-declare class ParagraphStyle--><!--Device-unnamed-declare class ParagraphStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value?: ParagraphStyleInterface)
```

A constructor used to create a text paragraph style.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-constructor(value?: ParagraphStyleInterface)--><!--Device-ParagraphStyle-constructor(value?: ParagraphStyleInterface)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ParagraphStyleInterface](arkts-arkui-paragraphstyleinterface-i.md) | No | Paragraph style setting item.<br>Default value: If not passed, the default values of the properties of **ParagraphStyleInterface** are inherited. |

## leadingMargin

```TypeScript
readonly leadingMargin?: number | LeadingMarginPlaceholder
```

Indent of the styled string text paragraph.

When the return value is of the number type, the unit is vp.

**Type:** number &#124; [LeadingMarginPlaceholder](../arkts-components/arkts-arkui-richeditor-comp-leadingmarginplaceholder-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-readonly leadingMargin?: number | LeadingMarginPlaceholder--><!--Device-ParagraphStyle-readonly leadingMargin?: number | LeadingMarginPlaceholder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leadingMarginSpan

```TypeScript
readonly leadingMarginSpan?: LeadingMarginSpan
```

Custom indent information of the styled string text paragraph.

**Type:** [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ParagraphStyle-readonly leadingMarginSpan?: LeadingMarginSpan--><!--Device-ParagraphStyle-readonly leadingMarginSpan?: LeadingMarginSpan-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
readonly maxLines?: number
```

Maximum number of lines of the styled string text paragraph.

Value range: [0, INT32_MAX]. A negative value means no limit.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-readonly maxLines?: number--><!--Device-ParagraphStyle-readonly maxLines?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
readonly overflow?: TextOverflow
```

Display mode of the styled string text paragraph when it is too long.

Default value: **TextOverflow.None**.

It must be used together with **maxLines**; setting it alone does not take effect. **TextOverflow.MARQUEE** is not supported.

**Type:** [TextOverflow](arkts-arkui-textoverflow-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-readonly overflow?: TextOverflow--><!--Device-ParagraphStyle-readonly overflow?: TextOverflow-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
readonly paragraphSpacing?: number
```

Paragraph spacing of the styled string text paragraph.

Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ParagraphStyle-readonly paragraphSpacing?: number--><!--Device-ParagraphStyle-readonly paragraphSpacing?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
readonly shaderStyle?: ShaderStyle
```

Text shader effect.

**Note:** When this API is set together with **strokeWidth** of [TextStyleInterface](arkts-arkui-textstyleinterface-i.md), this API does not take effect. **shaderStyle** has a higher priority than **fontColor** in [TextStyleInterface](arkts-arkui-textstyleinterface-i.md).

**Type:** [ShaderStyle](arkts-arkui-shaderstyle-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ParagraphStyle-readonly shaderStyle?: ShaderStyle--><!--Device-ParagraphStyle-readonly shaderStyle?: ShaderStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tailIndents

```TypeScript
readonly tailIndents?: Array<number>
```

Tail indent distance of the styled string text paragraph. INT32_MAX] The value **0** means no tail indent. **Note:** In the same paragraph, the **tailIndents** array takes values by array index in sequence for each line to perform indentation. For the first line of a new paragraph, the value is taken again from index 0 of the **tailIndents** array. Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units).

**Type:** Array&lt;number&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ParagraphStyle-readonly tailIndents?: Array<number>--><!--Device-ParagraphStyle-readonly tailIndents?: Array<number>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
readonly textAlign?: TextAlign
```

Horizontal alignment of the styled string text paragraph.

**Note:** **textAlign** can only adjust the overall layout of the text and does not affect the display order of characters.

**Type:** [TextAlign](arkts-arkui-textalign-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-readonly textAlign?: TextAlign--><!--Device-ParagraphStyle-readonly textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
readonly textDirection?: TextDirection
```

Text direction.

**Type:** [TextDirection](arkts-arkui-textdirection-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ParagraphStyle-readonly textDirection?: TextDirection--><!--Device-ParagraphStyle-readonly textDirection?: TextDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
readonly textIndent?: number
```

First-line text indent of the styled string text paragraph. Unit: [vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#basic-pixel-units)

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-readonly textIndent?: number--><!--Device-ParagraphStyle-readonly textIndent?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
readonly textVerticalAlign?: TextVerticalAlign
```

Vertical alignment of the styled string text paragraph.

The effect differs only when the same font size is used in a paragraph and the line height [lineHeight](../arkts-components/arkts-arkui-text-comp-attribute.md#lineheight) is set at the same time, or when text of different font sizes is mixed in the same paragraph. Otherwise, setting any enum value of this attribute produces the same layout effect as not setting it. The **SuperscriptStyle** superscript and subscript style in [TextStyle](arkts-arkui-textstyle-c.md) of the styled string takes effect only when the value of TextVerticalAlign is **TextVerticalAlign.BASELINE**. With other vertical alignment modes, superscript and subscript text behaves the same as normal text, with no superscript or subscript effect.

**Type:** [TextVerticalAlign](arkts-arkui-textverticalalign-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ParagraphStyle-readonly textVerticalAlign?: TextVerticalAlign--><!--Device-ParagraphStyle-readonly textVerticalAlign?: TextVerticalAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
readonly wordBreak?: WordBreak
```

Line break rule of the styled string text paragraph.

**Type:** [WordBreak](arkts-arkui-wordbreak-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyle-readonly wordBreak?: WordBreak--><!--Device-ParagraphStyle-readonly wordBreak?: WordBreak-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
