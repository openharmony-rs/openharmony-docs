# ParagraphStyleInterface

```TypeScript
declare interface ParagraphStyleInterface
```

ParagraphStyleInterface

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leadingMargin

```TypeScript
leadingMargin?: LengthMetrics | LeadingMarginPlaceholder
```

Indent of the text paragraph. The value cannot be in percentage.

Default value: **0**.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; [LeadingMarginPlaceholder](../arkts-components/arkts-arkui-richeditor-comp-leadingmarginplaceholder-i.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leadingMarginSpan

```TypeScript
leadingMarginSpan?: LeadingMarginSpan
```

Custom indentation information for text paragraphs. The value cannot be in percentage.

Default value: **0**.

**Type:** [LeadingMarginSpan](arkts-arkui-leadingmarginspan-c.md)

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: number
```

Maximum number of lines in the text paragraph. By default, the number of lines is not limited.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

Display mode when the text is too long in the text paragraph.

Default value: **TextOverflow.None**.

This parameter must be used with **maxLines** for the settings to take effect. **TextOverflow.MARQUEE** is not supported.

**Type:** [TextOverflow](arkts-arkui-textoverflow-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
paragraphSpacing?: LengthMetrics
```

Paragraph spacing of the styled string text.

Default value: **0**. The value cannot be in percentage.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
shaderStyle?: ShaderStyle
```

Text shader effect.

This API does not take effect when used together with [TextStyleInterface](arkts-arkui-textstyleinterface-i.md) **strokeWidth**. **shaderStyle** has a higher priority than [TextStyleInterface](arkts-arkui-textstyleinterface-i.md) **fontColor**.

**Since**: 26.0.0.

**Type:** [ShaderStyle](arkts-arkui-shaderstyle-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tailIndents

```TypeScript
tailIndents?: LengthMetrics | Array<LengthMetrics>
```

Specify the tail indentation for each line in a paragraph.

<p>&lt;strong&gt;NOTE&lt;/strong&gt;: <br>When a single LengthMetrics value is provided, all lines share the same tail indent. <br>When an array is provided, the i-th element specifies the tail indent for the i-th line. If the number of text lines exceeds the array length, the last element in the array is used for the remaining lines. <br>Negative values are treated as 0. </p>

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md) &#124; Array&lt;[LengthMetrics](arkts-arkui-lengthmetrics-t.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Horizontal alignment of the text paragraph.

Default value: **TextAlign.Start**.

**Type:** [TextAlign](arkts-arkui-textalign-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: LengthMetrics
```

First line indent of the text paragraph. The value cannot be in percentage.

Default value: **0**.

**Type:** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
textVerticalAlign?: TextVerticalAlign
```

Vertical alignment mode of text paragraphs.

Default value: **TextVerticalAlign.BASELINE**.

**Type:** [TextVerticalAlign](arkts-arkui-textverticalalign-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

Word break rule of the text paragraph.

Default value: **WordBreak.NORMAL**.

**Type:** [WordBreak](arkts-arkui-wordbreak-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
