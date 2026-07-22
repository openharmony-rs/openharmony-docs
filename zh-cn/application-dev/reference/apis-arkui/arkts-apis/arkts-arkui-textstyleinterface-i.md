# TextStyleInterface

TextStyleInterface

**起始版本：** 12

<!--Device-unnamed-declare interface TextStyleInterface--><!--Device-unnamed-declare interface TextStyleInterface-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontColor

```TypeScript
fontColor?: ResourceColor
```

字体颜色。

默认为主题色。

**类型：** ResourceColor

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontColor?: ResourceColor--><!--Device-TextStyleInterface-fontColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontConfigs

```TypeScript
fontConfigs?: FontConfigs
```

字体配置。默认值继承[FontConfigs](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#fontconfigs24对象说明)。

**类型：** FontConfigs

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontConfigs?: FontConfigs--><!--Device-TextStyleInterface-fontConfigs?: FontConfigs-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: ResourceStr
```

文本字体。

默认为主题字体。

**类型：** ResourceStr

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontFamily?: ResourceStr--><!--Device-TextStyleInterface-fontFamily?: ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

字体大小。

默认字体大小为16fp。

如果LengthMetrics的unit值是PERCENT，当前设置不生效，处理为16fp。

单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) 

**类型：** LengthMetrics

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontSize?: LengthMetrics--><!--Device-TextStyleInterface-fontSize?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

字体样式。

默认值：FontStyle.Normal

**类型：** FontStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontStyle?: FontStyle--><!--Device-TextStyleInterface-fontStyle?: FontStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontVariations

```TypeScript
fontVariations?: Array<FontVariation>
```

可变字体的属性。

默认值：undefined，表示未设置可变字体的属性。

fontVariations属性的优先级高于fontWeight。

**类型：** Array&lt;FontVariation&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontVariations?: Array<FontVariation>--><!--Device-TextStyleInterface-fontVariations?: Array<FontVariation>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

字体粗细。

number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。

**类型：** number \| FontWeight \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-fontWeight?: number | FontWeight | string--><!--Device-TextStyleInterface-fontWeight?: number | FontWeight | string-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

文本描边颜色。

默认值为字体颜色，设置异常值时取字体颜色。

**类型：** ResourceColor

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-strokeColor?: ResourceColor--><!--Device-TextStyleInterface-strokeColor?: ResourceColor-End-->

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

<!--Device-TextStyleInterface-strokeJoinStyle?: StrokeJoinStyle--><!--Device-TextStyleInterface-strokeJoinStyle?: StrokeJoinStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics
```

文本描边宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，处理为0。

设置值小于0时为实心字，大于0时为空心字。

默认值为0。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-strokeWidth?: LengthMetrics--><!--Device-TextStyleInterface-strokeWidth?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## superscript

```TypeScript
superscript?: SuperscriptStyle
```

文本上下角标。

默认值：SuperscriptStyle.NORMAL

**类型：** SuperscriptStyle

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-TextStyleInterface-superscript?: SuperscriptStyle--><!--Device-TextStyleInterface-superscript?: SuperscriptStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

