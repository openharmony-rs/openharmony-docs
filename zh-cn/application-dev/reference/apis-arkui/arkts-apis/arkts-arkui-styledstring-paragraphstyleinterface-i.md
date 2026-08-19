# ParagraphStyleInterface

段落样式

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface ParagraphStyleInterface--><!--Device-unnamed-export declare interface ParagraphStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leadingMargin

```TypeScript
leadingMargin?: LengthMetrics | LeadingMarginPlaceholder
```

设置文本段落的缩进。不支持百分比。 默认值：0

**类型：** [LengthMetrics](arkts-arkui-lengthmetrics-t.md) \| [LeadingMarginPlaceholder](arkts-arkui-richeditor-leadingmarginplaceholder-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-leadingMargin?: LengthMetrics | LeadingMarginPlaceholder--><!--Device-ParagraphStyleInterface-leadingMargin?: LengthMetrics | LeadingMarginPlaceholder-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## leadingMarginSpan

```TypeScript
leadingMarginSpan?: LeadingMarginSpan
```

设置文本段落的自定义缩进。不支持百分比。 默认值：0

**类型：** [LeadingMarginSpan](arkts-arkui-styledstring-leadingmarginspan-c.md)

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-leadingMarginSpan?: LeadingMarginSpan--><!--Device-ParagraphStyleInterface-leadingMarginSpan?: LeadingMarginSpan-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## maxLines

```TypeScript
maxLines?: int
```

设置文本段落的最大行数，默认不限制。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-maxLines?: int--><!--Device-ParagraphStyleInterface-maxLines?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## overflow

```TypeScript
overflow?: TextOverflow
```

设置文本段落超长时的显示方式。 默认值：TextOverflow.None 需配合maxLines使用，单独设置不生效。不支持TextOverflow.MARQUEE。

**类型：** [TextOverflow](arkts-arkui-textoverflow-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-overflow?: TextOverflow--><!--Device-ParagraphStyleInterface-overflow?: TextOverflow-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## paragraphSpacing

```TypeScript
paragraphSpacing?: LengthMetrics
```

设置文本段落的段落间距。 段落间距默认大小为0。不支持百分比。

**类型：** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-paragraphSpacing?: LengthMetrics--><!--Device-ParagraphStyleInterface-paragraphSpacing?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## shaderStyle

```TypeScript
shaderStyle?: ShaderStyle
```

设置文本着色器效果。 该接口与[TextStyleInterface](arkts-arkui-styledstring-textstyleinterface-i.md)的strokeWidth同时设置时，该接口不生效。

**类型：** [ShaderStyle](arkts-arkui-textcommon-shaderstyle-c.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-shaderStyle?: ShaderStyle--><!--Device-ParagraphStyleInterface-shaderStyle?: ShaderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tailIndents

```TypeScript
tailIndents?: LengthMetrics | Array<LengthMetrics>
```

设置文本段落的文本尾部缩进。当提供一个单独的LengthMetrics值时，所有行共享相同的尾部缩进；当提供一个数组时，第i个元素指定第i行的尾部缩进；如果文本行数超过数组长度，则数组中的最后一个元素将用于剩余的行。 默认值：0

**类型：** [LengthMetrics](arkts-arkui-lengthmetrics-t.md) \| Array&lt;[LengthMetrics](arkts-arkui-lengthmetrics-t.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-tailIndents?: LengthMetrics | Array<LengthMetrics>--><!--Device-ParagraphStyleInterface-tailIndents?: LengthMetrics | Array<LengthMetrics>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textAlign

```TypeScript
textAlign?: TextAlign
```

设置文本段落在水平方向的对齐方式。 默认值：TextAlign.Start

**类型：** [TextAlign](arkts-arkui-textalign-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-textAlign?: TextAlign--><!--Device-ParagraphStyleInterface-textAlign?: TextAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textDirection

```TypeScript
textDirection?: TextDirection
```

设置文本方向。 默认值：TextDirection.DEFAULT

**类型：** [TextDirection](arkts-arkui-textcommon-textdirection-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-textDirection?: TextDirection--><!--Device-ParagraphStyleInterface-textDirection?: TextDirection-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textIndent

```TypeScript
textIndent?: LengthMetrics
```

设置文本段落的首行文本缩进。不支持百分比。 默认值：0

**类型：** [LengthMetrics](arkts-arkui-lengthmetrics-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-textIndent?: LengthMetrics--><!--Device-ParagraphStyleInterface-textIndent?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textVerticalAlign

```TypeScript
textVerticalAlign?: TextVerticalAlign
```

设置文本段落在垂直方向的对齐方式。 默认值：TextVerticalAlign.BASELINE

**类型：** [TextVerticalAlign](arkts-arkui-textcommon-textverticalalign-e.md)

**起始版本：** 24

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为24。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-textVerticalAlign?: TextVerticalAlign--><!--Device-ParagraphStyleInterface-textVerticalAlign?: TextVerticalAlign-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## wordBreak

```TypeScript
wordBreak?: WordBreak
```

设置文本段落的断行规则。 默认值：WordBreak.NORMAL

**类型：** [WordBreak](arkts-arkui-wordbreak-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ParagraphStyleInterface-wordBreak?: WordBreak--><!--Device-ParagraphStyleInterface-wordBreak?: WordBreak-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

