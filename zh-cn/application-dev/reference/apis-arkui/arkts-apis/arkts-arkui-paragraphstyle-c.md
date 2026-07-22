# ParagraphStyle

文本段落样式对象说明。

除首个段落外，后续段落按'\n'划分。

每个段落的段落样式按首个占位设置的段落样式生效，未设置时，段落按被绑定组件的段落样式生效。

在API版本26.0.0之前，如果属性字符串段落内首个占位为[CustomSpan](arkts-arkui-customspan-c.md)或[ImageAttachment](arkts-arkui-imageattachment-c.md)时，设置在该段落上的段落样式不生效。从API版本26.0.0开始，设置段落样式生效。

**起始版本：** 12

<!--Device-unnamed-declare class ParagraphStyle--><!--Device-unnamed-declare class ParagraphStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(value?: ParagraphStyleInterface)
```

文本段落样式的构造函数。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-constructor(value?: ParagraphStyleInterface)--><!--Device-ParagraphStyle-constructor(value?: ParagraphStyleInterface)-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ParagraphStyleInterface](arkts-arkui-paragraphstyleinterface-i.md) | 否 | 段落样式设置项。 |

## leadingMargin

```TypeScript
readonly leadingMargin?: number | LeadingMarginPlaceholder
```

获取属性字符串文本段落的缩进。

返回为number类型时，单位为vp。

**类型：** number \| LeadingMarginPlaceholder

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly leadingMargin?: number | LeadingMarginPlaceholder--><!--Device-ParagraphStyle-readonly leadingMargin?: number | LeadingMarginPlaceholder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leadingMarginSpan

```TypeScript
readonly leadingMarginSpan?: LeadingMarginSpan
```

获取属性字符串文本段落的自定义缩进信息。

**类型：** LeadingMarginSpan

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly leadingMarginSpan?: LeadingMarginSpan--><!--Device-ParagraphStyle-readonly leadingMarginSpan?: LeadingMarginSpan-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
readonly maxLines?: number
```

获取属性字符串文本段落的最大行数。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly maxLines?: number--><!--Device-ParagraphStyle-readonly maxLines?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
readonly overflow?: TextOverflow
```

获取属性字符串文本段落超长时的显示方式。

**类型：** TextOverflow

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly overflow?: TextOverflow--><!--Device-ParagraphStyle-readonly overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
readonly paragraphSpacing?: number
```

获取属性字符串文本段落的段落间距。

单位：vp

**类型：** number

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly paragraphSpacing?: number--><!--Device-ParagraphStyle-readonly paragraphSpacing?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
readonly shaderStyle?: ShaderStyle
```

获取文本着色器效果。

**类型：** ShaderStyle

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly shaderStyle?: ShaderStyle--><!--Device-ParagraphStyle-readonly shaderStyle?: ShaderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tailIndents

```TypeScript
readonly tailIndents?: Array<number>
```

获取StyledString的尾部缩进。单位为vp。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly tailIndents?: Array<number>--><!--Device-ParagraphStyle-readonly tailIndents?: Array<number>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
readonly textAlign?: TextAlign
```

获取属性字符串文本段落在水平方向的对齐方式。

**类型：** TextAlign

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly textAlign?: TextAlign--><!--Device-ParagraphStyle-readonly textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
readonly textDirection?: TextDirection
```

获取文本方向。

**类型：** TextDirection

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly textDirection?: TextDirection--><!--Device-ParagraphStyle-readonly textDirection?: TextDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
readonly textIndent?: number
```

获取属性字符串文本段落的首行文本缩进。单位VP

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly textIndent?: number--><!--Device-ParagraphStyle-readonly textIndent?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
readonly textVerticalAlign?: TextVerticalAlign
```

获取属性字符串文本段落在垂直方向的对齐方式。

一个段落下使用同一字号必须同时设置行高[lineHeight](TextAttribute#lineHeight)或者同一个段落不同字号文本混排时才有效果差异，否则设置了该属性任意枚举值和未设置该属性都是一样的排版效果。属性字符串[TextStyle](arkts-arkui-textstyle-c.md)中的SuperscriptStyle上下角标样式仅在[TextVerticalAlign](arkts-arkui-textverticalalign-e.md)属性值为TextVerticalAlign.BASELINE时生效，其余垂直对齐方式下上下角标文本和普通文本表现一致，无上下角标效果。

**类型：** TextVerticalAlign

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly textVerticalAlign?: TextVerticalAlign--><!--Device-ParagraphStyle-readonly textVerticalAlign?: TextVerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
readonly wordBreak?: WordBreak
```

获取属性字符串文本段落的断行规则。

**类型：** WordBreak

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-ParagraphStyle-readonly wordBreak?: WordBreak--><!--Device-ParagraphStyle-readonly wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

