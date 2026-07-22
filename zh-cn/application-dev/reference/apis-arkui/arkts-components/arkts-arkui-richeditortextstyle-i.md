# RichEditorTextStyle

文本样式信息。

**起始版本：** 10

<!--Device-unnamed-declare interface RichEditorTextStyle--><!--Device-unnamed-declare interface RichEditorTextStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration?: DecorationStyleInterface
```

设置文本装饰线的样式、颜色和粗细。

type默认值：TextDecorationType.None

color默认值：跟随字体颜色。

style默认值：TextDecorationStyle.SOLID

thicknessScale默认值：1.0

**类型：** DecorationStyleInterface

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-decoration?: DecorationStyleInterface--><!--Device-RichEditorTextStyle-decoration?: DecorationStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

文本颜色。

默认值：$r('sys.color.font_primary')。当[shaderStyle](arkts-arkui-richeditorparagraphstyle-i.md)同时设置时，shaderStyle优先级高于fontColor。

**类型：** ResourceColor

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-fontColor?: ResourceColor--><!--Device-RichEditorTextStyle-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: ResourceStr
```

设置字体列表，当前支持'HarmonyOS Sans'字体和[注册自定义字体](../arkts-apis/arkts-font.md)。默认字体:'HarmonyOS Sans'。

**类型：** ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-fontFamily?: ResourceStr--><!--Device-RichEditorTextStyle-fontFamily?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFeature

```TypeScript
fontFeature?: string
```

设置文字特性效果，比如数字等宽的特性。如果未设置，默认为变宽数字。设置无效字符保持默认。

格式为：normal | &lt;feature-tag-value&gt;

&lt;feature-tag-value&gt;的格式为：<string> [ <integer> | on | off ]

&lt;feature-tag-value&gt;的个数可以有多个，中间用','隔开。

例如，使用等宽时钟数字的输入格式为："ss01" on。

Font Feature当前支持的属性见[fontFeature](TextAttribute#fontFeature)属性列表。

设置 Font Feature 属性，Font Feature 是 OpenType 字体的高级排版能力，如支持连字、数字等宽等特性，一般用在自定义字体中，其能力需要字体本身支持。

更多 Font Feature 能力介绍可参考 https://www.w3.org/TR/css-fonts-3/#font-feature-settings-prop 和 https://sparanoid.com/lab/opentype-features/

**类型：** string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-fontFeature?: string--><!--Device-RichEditorTextStyle-fontFeature?: string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: Length | number
```

设置字体大小，Length为number类型时，使用fp单位。number类型取值范围：(0, +∞)。设置为0或负值时，按默认值处理。字体默认大小为16fp。不支持设置百分比字符串。

**类型：** Length \| number

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-fontSize?: Length | number--><!--Device-RichEditorTextStyle-fontSize?: Length | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

字体样式。

默认值：FontStyle.Normal。

**类型：** FontStyle

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-fontStyle?: FontStyle--><!--Device-RichEditorTextStyle-fontStyle?: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

字体粗细。

number类型取值[100,900]，取值间隔为100，默认为400，取值越大，字体越粗。超出范围时按默认值400生效。

string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"分别对应FontWeight中相应的枚举值。

默认值：FontWeight.Normal。

**类型：** number \| FontWeight \| string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-fontWeight?: number | FontWeight | string--><!--Device-RichEditorTextStyle-fontWeight?: number | FontWeight | string-End-->

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

<!--Device-RichEditorTextStyle-halfLeading?: boolean--><!--Device-RichEditorTextStyle-halfLeading?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## letterSpacing

```TypeScript
letterSpacing?: number | string
```

设置文本字符间距，默认单位为fp。默认值：0。当取值为负值时，文字会发生压缩。

**类型：** number \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-letterSpacing?: number | string--><!--Device-RichEditorTextStyle-letterSpacing?: number | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## lineHeight

```TypeScript
lineHeight?: number | string | Resource
```

设置文本的文本行高。

默认值：不设置时自适应字体大小。

number类型取值范围：(0, +∞)，设置值不大于0时，不限制文本行高，自适应字体大小。number类型时单位为fp，不支持设置百分比字符串。当lineHeight设置值小于当前字号下文本渲染出的实际高度时，[fallbackLineSpacing](RichEditorAttribute#fallbackLineSpacing)属性将生效。

**类型：** number \| string \| Resource

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-lineHeight?: number | string | Resource--><!--Device-RichEditorTextStyle-lineHeight?: number | string | Resource-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

文本描边颜色。

默认值：跟随字体颜色。

设置异常值时跟随字体颜色。

**类型：** ResourceColor

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-strokeColor?: ResourceColor--><!--Device-RichEditorTextStyle-strokeColor?: ResourceColor-End-->

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

<!--Device-RichEditorTextStyle-strokeJoinStyle?: StrokeJoinStyle--><!--Device-RichEditorTextStyle-strokeJoinStyle?: StrokeJoinStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics | number
```

文本描边宽度。如果LengthMetrics的unit值是[PERCENT](../arkts-apis/arkts-arkui-graphics-lengthunit-e.md)，当前设置不生效，作为0处理。

值小于0时为实体字，大于0时为轮廓字，等于0时无描边效果。

默认值：0。

单位：LengthMetrics类型时跟随LengthMetrics，number类型时是vp。

取值范围：(-∞, +∞)

与[shaderStyle](arkts-arkui-richeditorparagraphstyle-i.md)同时设置时，shaderStyle不生效。

**类型：** LengthMetrics \| number

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-strokeWidth?: LengthMetrics | number--><!--Device-RichEditorTextStyle-strokeWidth?: LengthMetrics | number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textBackgroundStyle

```TypeScript
textBackgroundStyle?: TextBackgroundStyle
```

文本背景样式。

默认值：

{color: Color.Transparent,radius: 0}

**类型：** TextBackgroundStyle

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-textBackgroundStyle?: TextBackgroundStyle--><!--Device-RichEditorTextStyle-textBackgroundStyle?: TextBackgroundStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## textShadow

```TypeScript
textShadow?: ShadowOptions | Array<ShadowOptions>
```

设置文字阴影效果。

默认值：undefined，不设置文字阴影效果。

该接口支持以数组形式入参，实现多重文字阴影。

**说明：**

仅支持设置阴影模糊半径、颜色和偏移量，不支持智能取色。

**类型：** ShadowOptions \| Array&lt;ShadowOptions&gt;

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-RichEditorTextStyle-textShadow?: ShadowOptions | Array<ShadowOptions>--><!--Device-RichEditorTextStyle-textShadow?: ShadowOptions | Array<ShadowOptions>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

