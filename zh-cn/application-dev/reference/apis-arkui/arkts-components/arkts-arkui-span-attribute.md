# Span属性/事件

属性继承自[BaseSpan](arkts-arkui-basespan-c.md)。通用事件支持点击事件onClick、 悬浮事件onHover。@extends CommonMethod&lt;SpanAttribute&gt; [since 7 - 10] @extends BaseSpan&lt;SpanAttribute&gt; [since 11]

**继承/实现关系：** SpanAttribute extends BaseSpan<SpanAttribute>

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## decoration

```TypeScript
decoration(value: DecorationStyleInterface)
```

设置文本装饰线样式及其颜色。未通过该接口设置时，默认装饰线类型为TextDecorationType.None（无装饰线），颜色为Color.Black（黑色），样式为TextDecorationStyle.SOLID（实线）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](../arkts-apis/arkts-arkui-decorationstyleinterface-i.md) | 是 | 文本装饰线样式对象。    **说明：** style参数不支持卡片能力。<br>**起始版本：** 12 |

## font

```TypeScript
font(value: Font)
```

设置文本样式。包括字体大小、字体粗细、字体族和字体风格。

> **说明：**
> 
> fontWeight设置过大可能会在不同字体下有截断。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 文本样式，包括字体大小、字体粗细、字体族和字体风格。 |

## font

```TypeScript
font(value: Font, fontConfigs?: FontConfigs)
```

设置文本样式。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | Font | 是 | 文本样式，包括字体大小、字体粗细、字体族和字体风格。 |
| fontConfigs | [FontConfigs](../arkts-apis/arkts-arkui-fontconfigs-i.md) | 否 | 字体配置，用于自定义字体渲染行为（如配置可变字体属性）。当需要对字体进行高级配置时传入此参数，不传入时继承 [FontConfigs](../arkts-apis/arkts-arkui-fontconfigs-i.md)的默认配置。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。未通过该接口设置时，默认字体颜色为'#FF182431'（深灰色），Wearable设备上默认为'#C5FFFFFF'（白色，不透明度约为77%）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。 |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

设置字体列表。未通过该接口设置时，默认字体为'HarmonyOS Sans'。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 字体列表。 使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。例如：'Arial,HarmonyOS Sans'。 |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

设置字体大小。未通过该接口设置时，默认字体大小为16fp，Wearable设备上默认为15fp。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 字体大小。fontSize为number类型时，使用fp单位。string类型支持number类型取值的字符串形式，可以附带单位，例如"1 0"、"10fp"，不支持设置百分比字符串。 从API version 20开始，支持Resource类型。 |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。未通过该接口设置时，默认字体样式为FontStyle.Normal（正常样式）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FontStyle | 是 | 字体样式。 |

## fontVariations

```TypeScript
fontVariations(fontVariations: Array<FontVariation>)
```

设置可变字体的属性，适用于需要动态调整字体粗细、宽度等可变维度参数的场景。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontVariations | Array &lt;FontVariation&gt; | 是 | 可变字体的属性数组，每个数组元素包含axis（属性轴名称）和value（属性值）两个字段。fontVariations属性的优先级高 于[fontWeight](#fontweight)。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

设置文本的字体粗细，设置过大可能会在不同字体下有截断。未通过该接口设置时，默认字体粗细为FontWeight.Normal（正常粗细，对应数值400）。

> **说明：**
> 
> 当同时设置[fontVariations属性](#fontvariations)时，fontVariations属性的优先级更高。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 文本的字体粗细。 number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“ regular”、“medium”，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。传入超出取值范围或不符合间隔要求的值时取默认值。 从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |

## fontWeight

```TypeScript
fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

设置文本的字体粗细。未通过该接口设置时，默认字体粗细为FontWeight.Normal（正常粗细，对应数值400）。

> **说明：**
> 
> 当同时设置fontVariations属性时，fontVariations属性的优先级更高。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| weight | number \| FontWeight \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 文本的字体粗细。 number类型取值[100, 900]，取值间隔为100，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如“400”，以及“bold”、“bolder”、“lighter”、“ regular”、“medium”，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。 传入超出取值范围的值时取默认值。传入不符合间隔要求的值时，若设置fontWeightConfigs的enableVariableFontWeight为true，使用传入值；若设置为false，使用默认值。 |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | 否 | 字体粗细配置对象，用于配置可变字体字重等选项。默认值继承 [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md)。 |

## letterSpacing

```TypeScript
letterSpacing(value: number | ResourceStr)
```

设置文本字符间距。取值小于0，字符聚集重叠，取值大于0且随着数值变大，字符间距越来越大，稀疏分布。适用于标题排版、标签文字等需要调整字符紧凑度或稀疏度的场景。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | 是 | 文本字符间距。 单位：[fp](../arkts-apis/arkts-arkui-length-t.md) 从API version 20开始，支持Resource类型。<br>**起始版本：** 20 |

## lineHeight

```TypeScript
lineHeight(value: Length)
```

设置文本行高。未通过该接口设置时，默认由系统根据字体大小自动计算行高。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 文本行高。 number类型时单位为fp。设置string类型时，支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"，不支持设置百分比字符串。 |

## textCase

```TypeScript
textCase(value: TextCase)
```

设置文本大小写。未通过该接口设置时，默认文本大小写为TextCase.Normal（正常大小写）。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextCase](../arkts-apis/arkts-arkui-textcase-e.md) | 是 | 文本大小写。 |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

设置文字阴影效果。该接口支持以数组形式入参，实现多重文字阴影。不支持fill字段，不支持智能取色模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-shadowoptions-i.md) \| Array&lt;[ShadowOptions](arkts-arkui-shadowoptions-i.md)&gt; | 是 | 文字阴影效果。可设置阴影的模糊半径(radius)、颜色(color)、偏移距离(offsetX/offsetY)等参 数，支持数组形式实现多重阴影。 |
