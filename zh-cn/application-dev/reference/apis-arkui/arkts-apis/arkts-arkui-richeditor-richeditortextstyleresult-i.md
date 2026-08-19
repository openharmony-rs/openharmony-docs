# RichEditorTextStyleResult

后端返回的文本样式信息。 在RichEditorTextStyle中，fontWeight是设置字体粗细的输入参数。 而在RichEditorTextStyleResult中，会将之前设置的字体粗细转换为数字后返回。 转换关系如下： | RichEditorTextStyle中的fontWeight | RichEditorTextStyleResult中的fontWeight | | ---- | ----------------------------------- | | 100 | 0 | | 200 | 1 | | 300 | 2 | | 400 | 3 | | 500 | 4 | | 600 | 5 | | 700 | 6 | | 800 | 7 | | 900 | 8 | | Lighter | 12 | | Normal | 10 | | Regular | 14 | | Medium | 13 | | Bold | 9 | | Bolder | 11 | RichEditorSymbolSpanStyle和RichEditorSymbolSpanStyleResult中fontWeight的转换关系，与RichEditorTextStyle和 RichEditorTextStyleResult中fontWeight的转换关系一致。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface RichEditorTextStyleResult--><!--Device-unnamed-export declare interface RichEditorTextStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration: DecorationStyleResult
```

文本装饰线样式信息。

**类型：** [DecorationStyleResult](arkts-arkui-textcommon-decorationstyleresult-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-decoration: DecorationStyleResult--><!--Device-RichEditorTextStyleResult-decoration: DecorationStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

文本颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-fontColor: ResourceColor--><!--Device-RichEditorTextStyleResult-fontColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily: string
```

字体列表。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-fontFamily: string--><!--Device-RichEditorTextStyleResult-fontFamily: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: string
```

文字特性效果。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-fontFeature?: string--><!--Device-RichEditorTextStyleResult-fontFeature?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: double
```

字体大小，默认单位为fp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-fontSize: double--><!--Device-RichEditorTextStyleResult-fontSize: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle: FontStyle
```

字体样式。

**类型：** [FontStyle](arkts-arkui-fontstyle-e.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-fontStyle: FontStyle--><!--Device-RichEditorTextStyleResult-fontStyle: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: int
```

字体粗细。

**类型：** int

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-fontWeight: int--><!--Device-RichEditorTextStyleResult-fontWeight: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## halfLeading

```TypeScript
halfLeading?: boolean
```

文本是否将行间距平分至行的顶部与底部。 true表示将行间距平分至行的顶部与底部，false则不平分。 默认值：false。

**类型：** boolean

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-halfLeading?: boolean--><!--Device-RichEditorTextStyleResult-halfLeading?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: double
```

文本字符间距，默认单位为fp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-letterSpacing?: double--><!--Device-RichEditorTextStyleResult-letterSpacing?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: double
```

文本行高，默认单位为fp。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-lineHeight?: double--><!--Device-RichEditorTextStyleResult-lineHeight?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

文本描边颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-strokeColor?: ResourceColor--><!--Device-RichEditorTextStyleResult-strokeColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

文本描边拐角样式。 默认值：StrokeJoinStyle.MITER_JOIN。 **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** [StrokeJoinStyle](arkts-arkui-textcommon-strokejoinstyle-e.md)

**起始版本：** 26.0.0

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-strokeJoinStyle?: StrokeJoinStyle--><!--Device-RichEditorTextStyleResult-strokeJoinStyle?: StrokeJoinStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: double
```

文本描边宽度。 单位为[vp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。 **模型约束：** 此接口仅可在Stage模型下使用。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-strokeWidth?: double--><!--Device-RichEditorTextStyleResult-strokeWidth?: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textBackgroundStyle

```TypeScript
textBackgroundStyle?: TextBackgroundStyle
```

文本背景样式。

**类型：** [TextBackgroundStyle](../arkts-components/arkts-arkui-textbackgroundstyle-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-textBackgroundStyle?: TextBackgroundStyle--><!--Device-RichEditorTextStyleResult-textBackgroundStyle?: TextBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textShadow

```TypeScript
textShadow?: Array<ShadowOptions>
```

文字阴影效果。 **说明：** 仅支持查询阴影模糊半径、颜色和偏移量。

**类型：** Array&lt;[ShadowOptions](../arkts-components/arkts-arkui-shadowoptions-i.md)&gt;

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RichEditorTextStyleResult-textShadow?: Array<ShadowOptions>--><!--Device-RichEditorTextStyleResult-textShadow?: Array<ShadowOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

