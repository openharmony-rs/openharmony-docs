# RichEditorParagraphStyle

```TypeScript
declare interface RichEditorParagraphStyle
```

Defines the paragraph style.

**Since:** 11

<!--Device-unnamed-declare interface RichEditorParagraphStyle--><!--Device-unnamed-declare interface RichEditorParagraphStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## leadingMargin

```TypeScript
leadingMargin?: Dimension | LeadingMarginPlaceholder
```

Paragraph indentation. When a paragraph contains only ImageSpan or BuilderSpan, this attribute does not take effect. When the parameter is of the Dimension type, setting it in percentage form is not supported, and the default unit is vp. Default value: {"size":["0.00px","0.00px"]}

**Type:** [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) &#124; [LeadingMarginPlaceholder](arkts-arkui-richeditor-comp-leadingmarginplaceholder-i.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorParagraphStyle-leadingMargin?: Dimension | LeadingMarginPlaceholder--><!--Device-RichEditorParagraphStyle-leadingMargin?: Dimension | LeadingMarginPlaceholder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## lineBreakStrategy

```TypeScript
lineBreakStrategy?: LineBreakStrategy
```

Line break rule.

Default value: **LineBreakStrategy.GREEDY**

This parameter takes effect when **wordBreak** is not set to **breakAll**. Hyphens are not supported.

**Type:** [LineBreakStrategy](../arkts-apis/arkts-arkui-linebreakstrategy-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorParagraphStyle-lineBreakStrategy?: LineBreakStrategy--><!--Device-RichEditorParagraphStyle-lineBreakStrategy?: LineBreakStrategy-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
paragraphSpacing?: number
```

Paragraph spacing.

Unit: fp

Value range: [0, +∞). If a negative value is passed in, the default value is used.

The default paragraph spacing is 0.

**Type:** number

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-RichEditorParagraphStyle-paragraphSpacing?: number--><!--Device-RichEditorParagraphStyle-paragraphSpacing?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
shaderStyle?: ShaderStyle
```

Text shader effect.

Default value: undefined, which means no shader effect is set.

When this API is set together with strokeWidth in [RichEditorTextStyle](arkts-arkui-richeditor-comp-richeditortextstyle-i.md), this API does not take effect, and shaderStyle has a higher priority than fontColor in [RichEditorTextStyle](arkts-arkui-richeditor-comp-richeditortextstyle-i.md).

**Type:** [ShaderStyle](../arkts-apis/arkts-arkui-shaderstyle-c.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-RichEditorParagraphStyle-shaderStyle?: ShaderStyle--><!--Device-RichEditorParagraphStyle-shaderStyle?: ShaderStyle-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

Horizontal alignment of the text paragraph.

Default value: **TextAlign.START**

**Type:** [TextAlign](../arkts-apis/arkts-arkui-textalign-e.md)

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorParagraphStyle-textAlign?: TextAlign--><!--Device-RichEditorParagraphStyle-textAlign?: TextAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
textDirection?: TextDirection
```

Text direction.

Default value: **TextDirection.DEFAULT**

**Type:** [TextDirection](../arkts-apis/arkts-arkui-textdirection-e.md)

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-RichEditorParagraphStyle-textDirection?: TextDirection--><!--Device-RichEditorParagraphStyle-textDirection?: TextDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
textVerticalAlign?: TextVerticalAlign
```

Vertical alignment mode of text paragraphs.

Default value: **TextVerticalAlign.BASELINE**.

**Type:** [TextVerticalAlign](../arkts-apis/arkts-arkui-textverticalalign-e.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-RichEditorParagraphStyle-textVerticalAlign?: TextVerticalAlign--><!--Device-RichEditorParagraphStyle-textVerticalAlign?: TextVerticalAlign-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

Line break rule.

Default value: WordBreak.BREAK_WORD.

**Type:** [WordBreak](../arkts-apis/arkts-arkui-wordbreak-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-RichEditorParagraphStyle-wordBreak?: WordBreak--><!--Device-RichEditorParagraphStyle-wordBreak?: WordBreak-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
