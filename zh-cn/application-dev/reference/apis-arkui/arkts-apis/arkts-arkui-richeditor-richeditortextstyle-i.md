# RichEditorTextStyle

文本样式信息。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export declare interface RichEditorTextStyle--><!--Device-unnamed-export declare interface RichEditorTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

文本装饰线样式信息。

**类型：** [DecorationStyleInterface](arkts-arkui-styledstring-decorationstyleinterface-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-decoration?: DecorationStyleInterface--><!--Device-RichEditorTextStyle-decoration?: DecorationStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

文本颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-fontColor?: ResourceColor--><!--Device-RichEditorTextStyle-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: ResourceStr
```

字体列表。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-fontFamily?: ResourceStr--><!--Device-RichEditorTextStyle-fontFamily?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: string
```

文字特性效果。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-fontFeature?: string--><!--Device-RichEditorTextStyle-fontFeature?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Length | double
```

字体大小，默认单位为fp。

**类型：** [Length](arkts-arkui-length-t.md) \| double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-fontSize?: Length | double--><!--Device-RichEditorTextStyle-fontSize?: Length | double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

字体样式。

**类型：** [FontStyle](arkts-arkui-fontstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-fontStyle?: FontStyle--><!--Device-RichEditorTextStyle-fontStyle?: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: int | FontWeight | string
```

字体粗细。

**类型：** int \| [FontWeight](arkts-arkui-fontweight-e.md) \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-fontWeight?: int | FontWeight | string--><!--Device-RichEditorTextStyle-fontWeight?: int | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## halfLeading

```TypeScript
halfLeading?: boolean
```

文本是否将行间距平分至行的顶部与底部。 true表示将行间距平分至行的顶部与底部，false则不平分。 默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-halfLeading?: boolean--><!--Device-RichEditorTextStyle-halfLeading?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: double | string
```

文本字符间距，默认单位为fp。

**类型：** double \| string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-letterSpacing?: double | string--><!--Device-RichEditorTextStyle-letterSpacing?: double | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: double | string | Resource
```

文本行高，默认单位为fp。

**类型：** double \| string \| [Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-lineHeight?: double | string | Resource--><!--Device-RichEditorTextStyle-lineHeight?: double | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

文本描边颜色。 默认值：跟随字体颜色。 设置异常值时跟随字体颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-strokeColor?: ResourceColor--><!--Device-RichEditorTextStyle-strokeColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

文本描边拐角样式。 默认值：StrokeJoinStyle.MITER_JOIN。 **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** [StrokeJoinStyle](arkts-arkui-textcommon-strokejoinstyle-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-strokeJoinStyle?: StrokeJoinStyle--><!--Device-RichEditorTextStyle-strokeJoinStyle?: StrokeJoinStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics | double
```

文本描边宽度。如果LengthMetrics的unit值是[PERCENT](../../apis-na/arkts-apis/arkts-na-graphics-lengthunit-e.md#LengthUnit)，当前设置不生效，作为0处理。 值小于0时为实体字，大于0时为轮廓字，等于0时无描边效果。 默认值：0vp。 单位：LengthMetrics类型时跟随LengthMetrics，number或double类型时是vp。 取值范围：(-∞, +∞) **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** [LengthMetrics](../../apis-na/arkts-apis/arkts-na-graphics-lengthmetrics-c.md) \| double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-strokeWidth?: LengthMetrics | double--><!--Device-RichEditorTextStyle-strokeWidth?: LengthMetrics | double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textBackgroundStyle

```TypeScript
textBackgroundStyle?: TextBackgroundStyle
```

文本背景样式。

**类型：** [TextBackgroundStyle](../arkts-components/arkts-arkui-textbackgroundstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-textBackgroundStyle?: TextBackgroundStyle--><!--Device-RichEditorTextStyle-textBackgroundStyle?: TextBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textShadow

```TypeScript
textShadow?: ShadowOptions | Array<ShadowOptions>
```

文字阴影效果。 **说明：** 仅支持查询阴影模糊半径、颜色和偏移量。

**类型：** [ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md) \| Array&lt;[ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyle-textShadow?: ShadowOptions | Array<ShadowOptions>--><!--Device-RichEditorTextStyle-textShadow?: ShadowOptions | Array<ShadowOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

