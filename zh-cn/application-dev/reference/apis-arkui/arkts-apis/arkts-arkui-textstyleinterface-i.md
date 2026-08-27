# TextStyleInterface

文本字体样式。

**起始版本：** 12

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## fontColor

```TypeScript
fontColor?: ResourceColor
```

字体颜色。默认为主题色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontConfigs

```TypeScript
fontConfigs?: FontConfigs
```

字体配置。默认值继承[FontConfigs](arkts-arkui-fontconfigs-i.md)。

**类型：** [FontConfigs](arkts-arkui-fontconfigs-i.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontFamily

```TypeScript
fontFamily?: ResourceStr
```

文本字体。默认为主题字体。

**类型：** [ResourceStr](arkts-arkui-resourcestr-t.md)

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: LengthMetrics
```

字体大小。默认字体大小为16fp。如果LengthMetrics的unit值是PERCENT，当前设置不生效，处理为16fp。单位：[fp](arkts-arkui-length-t.md) 

**类型：** LengthMetrics

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontStyle

```TypeScript
fontStyle?: FontStyle
```

字体样式。默认值：FontStyle.Normal

**类型：** FontStyle

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontVariations

```TypeScript
fontVariations?: Array<FontVariation>
```

可变字体的属性。默认值：undefined，表示未设置可变字体的属性。fontVariations属性的优先级高于fontWeight。

**类型：** Array&lt;FontVariation&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | string
```

字体粗细。number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。传入超出取值范围或不符合间隔要求的值时取默认值。默认值：FontWeight.Normal

**类型：** number \| FontWeight \| string

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeColor

```TypeScript
strokeColor?: ResourceColor
```

文本描边颜色。默认值为字体颜色，设置异常值时取字体颜色。

**类型：** [ResourceColor](arkts-arkui-resourcecolor-t.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeJoinStyle

```TypeScript
strokeJoinStyle?: StrokeJoinStyle
```

文本描边拐角样式。具体枚举及说明请参考StrokeJoinStyle。默认值：StrokeJoinStyle.MITER_JOIN。

**类型：** [StrokeJoinStyle](arkts-arkui-strokejoinstyle-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## strokeWidth

```TypeScript
strokeWidth?: LengthMetrics
```

文本描边宽度。如果LengthMetrics的unit值是PERCENT，当前设置不生效，处理为0。设置值小于0时为实心字，大于0时为空心字。默认值为0。

**类型：** LengthMetrics

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## superscript

```TypeScript
superscript?: SuperscriptStyle
```

文本上下角标。默认值：SuperscriptStyle.NORMAL

**类型：** [SuperscriptStyle](arkts-arkui-superscriptstyle-e.md)

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
