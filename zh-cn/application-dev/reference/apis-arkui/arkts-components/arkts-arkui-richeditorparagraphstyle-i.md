# RichEditorParagraphStyle

段落样式。

**起始版本：** 11

<!--Device-unnamed-declare interface RichEditorParagraphStyle--><!--Device-unnamed-declare interface RichEditorParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leadingMargin

```TypeScript
leadingMargin?: Dimension | LeadingMarginPlaceholder
```

设置文本段落缩进，当段落仅存在ImageSpan或BuilderSpan时，此属性值不生效。参数为Dimension类型时，不支持以Percentage形式设置，默认单位为vp。默认值：{"size":["0.00px","0.00px"]}

**类型：** Dimension \| LeadingMarginPlaceholder

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-leadingMargin?: Dimension | LeadingMarginPlaceholder--><!--Device-RichEditorParagraphStyle-leadingMargin?: Dimension | LeadingMarginPlaceholder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineBreakStrategy

```TypeScript
lineBreakStrategy?: LineBreakStrategy
```

设置折行规则。

默认值：LineBreakStrategy.GREEDY

在wordBreak不等于breakAll的时候生效，不支持连字符。

**类型：** LineBreakStrategy

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-lineBreakStrategy?: LineBreakStrategy--><!--Device-RichEditorParagraphStyle-lineBreakStrategy?: LineBreakStrategy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
paragraphSpacing?: number
```

设置段落间距大小。

单位：fp

取值范围：[0, +∞)。传入负值时，按默认值处理。

段落间距默认大小为0。

**类型：** number

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-paragraphSpacing?: number--><!--Device-RichEditorParagraphStyle-paragraphSpacing?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
shaderStyle?: ShaderStyle
```

设置文本着色器效果。

默认值：undefined，不设置着色器效果。

该接口与[RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md)中的strokeWidth同时设置时，该接口不生效，shaderStyle的优先级高于[RichEditorTextStyle](arkts-arkui-richeditortextstyle-i.md)的fontColor。

**类型：** ShaderStyle

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-shaderStyle?: ShaderStyle--><!--Device-RichEditorParagraphStyle-shaderStyle?: ShaderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

设置文本段落在水平方向的对齐方式。默认值：TextAlign.START

**类型：** TextAlign

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-textAlign?: TextAlign--><!--Device-RichEditorParagraphStyle-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
textDirection?: TextDirection
```

设置文本方向。

默认值：TextDirection.DEFAULT

**类型：** TextDirection

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-textDirection?: TextDirection--><!--Device-RichEditorParagraphStyle-textDirection?: TextDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
textVerticalAlign?: TextVerticalAlign
```

设置文本段落在垂直方向的对齐方式。

默认值：TextVerticalAlign.BASELINE

**类型：** TextVerticalAlign

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-textVerticalAlign?: TextVerticalAlign--><!--Device-RichEditorParagraphStyle-textVerticalAlign?: TextVerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

设置断行规则。

默认值：WordBreak.BREAK_WORD。

**类型：** WordBreak

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorParagraphStyle-wordBreak?: WordBreak--><!--Device-RichEditorParagraphStyle-wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

