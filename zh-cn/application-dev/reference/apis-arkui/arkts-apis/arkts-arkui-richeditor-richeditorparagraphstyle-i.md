# RichEditorParagraphStyle

段落样式。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RichEditorParagraphStyle--><!--Device-unnamed-export declare interface RichEditorParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leadingMargin

```TypeScript
leadingMargin?: Dimension | LeadingMarginPlaceholder
```

设置文本段落缩进，当段落仅存在ImageSpan或BuilderSpan时，此属性值不生效。参数为Dimension类型时，不支持以Percentage形式设置。默认值：{"size":["0.00px","0.00px"]}

**类型：** [Dimension](arkts-arkui-dimension-t.md) \| [LeadingMarginPlaceholder](arkts-arkui-richeditor-leadingmarginplaceholder-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-leadingMargin?: Dimension | LeadingMarginPlaceholder--><!--Device-RichEditorParagraphStyle-leadingMargin?: Dimension | LeadingMarginPlaceholder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineBreakStrategy

```TypeScript
lineBreakStrategy?: LineBreakStrategy
```

设置折行规则。 默认值：LineBreakStrategy.GREEDY 在wordBreak不等于breakAll的时候生效，不支持连字符。

**类型：** [LineBreakStrategy](arkts-arkui-linebreakstrategy-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-lineBreakStrategy?: LineBreakStrategy--><!--Device-RichEditorParagraphStyle-lineBreakStrategy?: LineBreakStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
paragraphSpacing?: double
```

设置段落间距大小。 单位：fp 段落间距默认大小为0。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-paragraphSpacing?: double--><!--Device-RichEditorParagraphStyle-paragraphSpacing?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
shaderStyle?: ShaderStyle
```

设置文本着色器效果。 该接口与[RichEditorTextStyle](arkts-arkui-richeditor-richeditortextstyleresult-i.md#RichEditorTextStyleResult)中的strokeWidth同时设置时，该接口不生效，shaderStyle的优先级高于 [RichEditorTextStyle](arkts-arkui-richeditor-richeditortextstyleresult-i.md#RichEditorTextStyleResult)的fontColor。 **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** [ShaderStyle](arkts-arkui-textcommon-shaderstyle-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-shaderStyle?: ShaderStyle--><!--Device-RichEditorParagraphStyle-shaderStyle?: ShaderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

设置文本段落在水平方向的对齐方式。默认值：TextAlign.START

**类型：** [TextAlign](arkts-arkui-textalign-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-textAlign?: TextAlign--><!--Device-RichEditorParagraphStyle-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
textDirection?: TextDirection
```

设置文本书写方向。 默认值：TextDirection.DEFAULT

**类型：** [TextDirection](arkts-arkui-textcommon-textdirection-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-textDirection?: TextDirection--><!--Device-RichEditorParagraphStyle-textDirection?: TextDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
textVerticalAlign?: TextVerticalAlign
```

设置文本段落在垂直方向的对齐方式。 默认值：TextVerticalAlign.BASELINE **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** [TextVerticalAlign](arkts-arkui-textcommon-textverticalalign-e.md)

**起始版本：** 24

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为24。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-textVerticalAlign?: TextVerticalAlign--><!--Device-RichEditorParagraphStyle-textVerticalAlign?: TextVerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

设置断行规则。 默认值：WordBreak.BREAK_WORD

**类型：** [WordBreak](arkts-arkui-wordbreak-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorParagraphStyle-wordBreak?: WordBreak--><!--Device-RichEditorParagraphStyle-wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

