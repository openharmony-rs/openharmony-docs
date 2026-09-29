# ParagraphStyleInterface

```TypeScript
declare interface ParagraphStyleInterface
```

ParagraphStyleInterface

**Since:** 12

<!--Device-unnamed-declare interface ParagraphStyleInterface--><!--Device-unnamed-declare interface ParagraphStyleInterface-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leadingMargin

```TypeScript
leadingMargin?: LengthMetrics | LeadingMarginPlaceholder
```

Indentation of the text paragraph. Percentage is not supported.

Default value: **0**

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; [LeadingMarginPlaceholder](../arkts-components/arkts-arkui-richeditor-comp-leadingmarginplaceholder-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyleInterface-leadingMargin?: LengthMetrics | LeadingMarginPlaceholder--><!--Device-ParagraphStyleInterface-leadingMargin?: LengthMetrics | LeadingMarginPlaceholder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leadingMarginSpan

```TypeScript
leadingMarginSpan?: LeadingMarginSpan
```

Custom indentation of the text paragraph. Percentage is not supported.

Default value: **0**

**Type:** [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ParagraphStyleInterface-leadingMarginSpan?: LeadingMarginSpan--><!--Device-ParagraphStyleInterface-leadingMarginSpan?: LeadingMarginSpan-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines of the text paragraph.

**Note:** This takes effect only in **Text**. It is recommended to set it on the component side.

No limit by default.

Value range: [0, INT32_MAX]. When a negative number is passed in, no limit is applied.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyleInterface-maxLines?: number--><!--Device-ParagraphStyleInterface-maxLines?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

Display mode when the text paragraph is too long.

**Note:** This takes effect only in **Text**. It is recommended to set it on the component side.

Default value: **TextOverflow.None**

It must be used together with **maxLines**; setting it alone does not take effect. **TextOverflow.MARQUEE** is not supported.

**Type:** [TextOverflow](arkts-arkui-textoverflow-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyleInterface-overflow?: TextOverflow--><!--Device-ParagraphStyleInterface-overflow?: TextOverflow-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
paragraphSpacing?: LengthMetrics
```

Paragraph spacing of the text paragraph.

The default paragraph spacing is 0. Percentage is not supported.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ParagraphStyleInterface-paragraphSpacing?: LengthMetrics--><!--Device-ParagraphStyleInterface-paragraphSpacing?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
shaderStyle?: ShaderStyle
```

Text shader effect.

**Default effect:** When not passed in, no shader effect is applied, and the color set by **fontColor** is used.

When this API is set together with **strokeWidth** of [TextStyleInterface](arkts-arkui-textstyleinterface-i.md), this API does not take effect, and **shaderStyle** has a higher priority than **fontColor** in [TextStyleInterface](arkts-arkui-textstyleinterface-i.md).

**Type:** [ShaderStyle](arkts-arkui-shaderstyle-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ParagraphStyleInterface-shaderStyle?: ShaderStyle--><!--Device-ParagraphStyleInterface-shaderStyle?: ShaderStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tailIndents

```TypeScript
tailIndents?: LengthMetrics | Array<LengthMetrics>
```

Tail indentation of the text paragraph. Percentage is not supported. When a single **LengthMetrics** value is provided, all lines share the same tail indentation; when an array is provided, the i-th element specifies the tail indentation of the i-th line; if the number of text lines exceeds the array length, the last element in the array is used for the remaining lines. Default value: **0**.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; Array&lt;[LengthMetrics](arkts-arkui-lengthmetrics-t.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ParagraphStyleInterface-tailIndents?: LengthMetrics | Array<LengthMetrics>--><!--Device-ParagraphStyleInterface-tailIndents?: LengthMetrics | Array<LengthMetrics>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Horizontal alignment of the text paragraph.

Default value: **TextAlign.Start**

**Type:** [TextAlign](arkts-arkui-textalign-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyleInterface-textAlign?: TextAlign--><!--Device-ParagraphStyleInterface-textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
textDirection?: TextDirection
```

Text direction.

Default value: **TextDirection.DEFAULT**

**Type:** [TextDirection](arkts-arkui-textdirection-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ParagraphStyleInterface-textDirection?: TextDirection--><!--Device-ParagraphStyleInterface-textDirection?: TextDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: LengthMetrics
```

First-line text indentation of the text paragraph. Percentage is not supported.

Default value: **0**

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyleInterface-textIndent?: LengthMetrics--><!--Device-ParagraphStyleInterface-textIndent?: LengthMetrics-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
textVerticalAlign?: TextVerticalAlign
```

Vertical alignment of the text paragraph.

Default value: **TextVerticalAlign.BASELINE**

**Type:** [TextVerticalAlign](arkts-arkui-textverticalalign-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ParagraphStyleInterface-textVerticalAlign?: TextVerticalAlign--><!--Device-ParagraphStyleInterface-textVerticalAlign?: TextVerticalAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

Line breaking rule of the text paragraph.

Default value: **WordBreak.NORMAL**

**Type:** [WordBreak](arkts-arkui-wordbreak-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ParagraphStyleInterface-wordBreak?: WordBreak--><!--Device-ParagraphStyleInterface-wordBreak?: WordBreak-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
