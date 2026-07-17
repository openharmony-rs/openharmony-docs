# RichEditorTextStyleResult

后端返回的文本样式信息。

在RichEditorTextStyle中，fontWeight是设置字体粗细的输入参数。

而在RichEditorTextStyleResult中，会将之前设置的字体粗细转换为数字后返回。

RichEditorSymbolSpanStyle和RichEditorSymbolSpanStyleResult中fontWeight的转换关系，与RichEditorTextStyle和RichEditorTextStyleResult中fontWeight的转换关系一致。

**起始版本：** 10

<!--Device-unnamed-declare interface RichEditorTextStyleResult--><!--Device-unnamed-declare interface RichEditorTextStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration: DecorationStyleResult
```

文本装饰线样式信息。

**类型：** DecorationStyleResult

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-decoration: DecorationStyleResult--><!--Device-RichEditorTextStyleResult-decoration: DecorationStyleResult-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor: ResourceColor
```

文本颜色。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-fontColor: ResourceColor--><!--Device-RichEditorTextStyleResult-fontColor: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily: string
```

字体列表。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-fontFamily: string--><!--Device-RichEditorTextStyleResult-fontFamily: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: string
```

文字特性效果。

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-fontFeature?: string--><!--Device-RichEditorTextStyleResult-fontFeature?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize: number
```

字体大小，默认单位为fp。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-fontSize: number--><!--Device-RichEditorTextStyleResult-fontSize: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle: FontStyle
```

字体样式。

**类型：** FontStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-fontStyle: FontStyle--><!--Device-RichEditorTextStyleResult-fontStyle: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight: number
```

字体粗细。

**类型：** number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-fontWeight: number--><!--Device-RichEditorTextStyleResult-fontWeight: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## halfLeading

```TypeScript
halfLeading?: boolean
```

文本是否将行间距平分至行的顶部与底部。

true表示将行间距平分至行的顶部与底部，false则不平分。

默认值：false。

**类型：** boolean

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-halfLeading?: boolean--><!--Device-RichEditorTextStyleResult-halfLeading?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number
```

文本字符间距，默认单位为fp。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-letterSpacing?: number--><!--Device-RichEditorTextStyleResult-letterSpacing?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number
```

文本行高，默认单位为fp。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-lineHeight?: number--><!--Device-RichEditorTextStyleResult-lineHeight?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

文本描边颜色。

**类型：** ResourceColor

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-strokeColor?: ResourceColor--><!--Device-RichEditorTextStyleResult-strokeColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

文本描边拐角样式。

默认值：StrokeJoinStyle.MITER_JOIN。

**类型：** StrokeJoinStyle

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-strokeJoinStyle?: StrokeJoinStyle--><!--Device-RichEditorTextStyleResult-strokeJoinStyle?: StrokeJoinStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: number
```

文本描边宽度。

单位为[vp](../../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位)。

**类型：** number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-strokeWidth?: number--><!--Device-RichEditorTextStyleResult-strokeWidth?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textBackgroundStyle

```TypeScript
textBackgroundStyle?: TextBackgroundStyle
```

文本背景样式。

**类型：** TextBackgroundStyle

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-textBackgroundStyle?: TextBackgroundStyle--><!--Device-RichEditorTextStyleResult-textBackgroundStyle?: TextBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textShadow

```TypeScript
textShadow?: Array<ShadowOptions>
```

文字阴影效果。

**说明：**

仅支持查询阴影模糊半径、颜色和偏移量。

**类型：** Array<ShadowOptions>

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyleResult-textShadow?: Array<ShadowOptions>--><!--Device-RichEditorTextStyleResult-textShadow?: Array<ShadowOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

