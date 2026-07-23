# Span属性/事件

属性继承自[BaseSpan](arkts-arkui-basespan-c.md)。

通用事件支持[点击事件onClick](arkts-arkui-commonmethod-c.md#onclick)、[悬浮事件onHover](arkts-arkui-commonmethod-c.md#onhover)。

**继承/实现关系：** SpanAttribute extends [BaseSpan<SpanAttribute>]

**起始版本：** 7

<!--Device-unnamed-declare class SpanAttribute extends BaseSpan<SpanAttribute>--><!--Device-unnamed-declare class SpanAttribute extends BaseSpan<SpanAttribute>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## decoration

```TypeScript
decoration(value: DecorationStyleInterface)
```

设置文本装饰线样式及其颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-decoration(value: DecorationStyleInterface): SpanAttribute--><!--Device-SpanAttribute-decoration(value: DecorationStyleInterface): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [DecorationStyleInterface](../arkts-apis/arkts-arkui-decorationstyleinterface-i.md) | 是 | 文本装饰线样式对象。<br/>默认值：<br/>{<br/> type: TextDecorationType.None,<br/> color: Color.Black,<br/> style: TextDecorationStyle.SOLID <br/>}<br/>**说明：** <br/>style参数不支持卡片能力。<br>**起始版本：** 12 |

## font

```TypeScript
font(value: Font)
```

设置文本样式。包括字体大小、字体粗细、字体族和字体风格。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SpanAttribute-font(value: Font): SpanAttribute--><!--Device-SpanAttribute-font(value: Font): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 文本样式。 |

## font

```TypeScript
font(value: Font, fontConfigs?: FontConfigs)
```

设置文本样式。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

<!--Device-SpanAttribute-font(value: Font, fontConfigs?: FontConfigs): SpanAttribute--><!--Device-SpanAttribute-font(value: Font, fontConfigs?: FontConfigs): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Font](../arkts-apis/arkts-arkui-arkui-uicontext-font-c.md) | 是 | 文本样式，包括字体大小、字体粗细、字体族和字体风格。 |
| fontConfigs | [FontConfigs](../arkts-apis/arkts-arkui-fontconfigs-i.md) | 否 | 字体配置。默认值继承[FontConfigs](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#fontconfigs24对象说明)。 |

## fontColor

```TypeScript
fontColor(value: ResourceColor)
```

设置字体颜色。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-fontColor(value: ResourceColor): SpanAttribute--><!--Device-SpanAttribute-fontColor(value: ResourceColor): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) | 是 | 字体颜色。<br/>默认值：'#e6182431'<br/>Wearable设备上默认值为：'#c5ffffff' |

## fontFamily

```TypeScript
fontFamily(value: string | Resource)
```

设置字体列表。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-fontFamily(value: string | Resource): SpanAttribute--><!--Device-SpanAttribute-fontFamily(value: string | Resource): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | string \| Resource | 是 | 字体列表。<br>默认字体'HarmonyOS Sans'。<br>使用多个字体时，请用逗号','分隔，字体的优先级按顺序生效。例如：'Arial,HarmonyOS Sans'。 |

## fontSize

```TypeScript
fontSize(value: number | string | Resource)
```

设置字体大小。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-fontSize(value: number | string | Resource): SpanAttribute--><!--Device-SpanAttribute-fontSize(value: number | string | Resource): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| string \| Resource | 是 | 字体大小。fontSize为number类型时，使用fp单位。字体默认大小16fp。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"，不支持设置百分比字符串。<br/>Wearable设备上默认值为：15fp |

## fontStyle

```TypeScript
fontStyle(value: FontStyle)
```

设置字体样式。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-fontStyle(value: FontStyle): SpanAttribute--><!--Device-SpanAttribute-fontStyle(value: FontStyle): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [FontStyle](../../apis-arkgraphics2d/arkts-apis/arkts-arkgraphics2d-text-fontstyle-e.md) | 是 | 字体样式。<br/>默认值：FontStyle.Normal |

## fontVariations

```TypeScript
fontVariations(fontVariations: Array<FontVariation>)
```

设置可变字体的属性。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-SpanAttribute-fontVariations(fontVariations: Array<FontVariation>): SpanAttribute--><!--Device-SpanAttribute-fontVariations(fontVariations: Array<FontVariation>): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fontVariations | Array&lt;FontVariation&gt; | 是 | 可变字体的属性数组，数组成员为可变字体的各种属性。fontVariations属性的优先级高于[fontWeight](SpanAttribute#fontWeight(weight: number \| FontWeight \| ResourceStr, fontWeightConfigs?: FontWeightConfigs))。 |

## fontWeight

```TypeScript
fontWeight(value: number | FontWeight | ResourceStr)
```

设置文本的字体粗细，设置过大可能会在不同字体下有截断。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-fontWeight(value: number | FontWeight | ResourceStr): SpanAttribute--><!--Device-SpanAttribute-fontWeight(value: number | FontWeight | ResourceStr): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| FontWeight \| ResourceStr | 是 | 文本的字体粗细，number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。<br/>默认值：FontWeight.Normal <br>从API version 20开始，支持[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)类型。<br>**起始版本：** 20 |

## fontWeight

```TypeScript
fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs)
```

设置文本的字体粗细。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本24开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本24开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SpanAttribute--><!--Device-SpanAttribute-fontWeight(weight: number | FontWeight | ResourceStr, fontWeightConfigs?: FontWeightConfigs): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| weight | number \| FontWeight \| ResourceStr | 是 | 文本的字体粗细，number类型取值[100, 900]，取值间隔为100，默认为400，取值越大，字体越粗。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。设置过大可能会在不同字体下有截断。<br/>默认值：FontWeight.Normal |
| fontWeightConfigs | [FontWeightConfigs](../arkts-apis/arkts-arkui-fontweightconfigs-i.md) | 否 | 字体粗细配置。默认值继承[FontWeightConfigs](../../../reference/apis-arkui/arkui-ts/ts-text-common.md#fontweightconfigs24对象说明)。 |

## letterSpacing

```TypeScript
letterSpacing(value: number | ResourceStr)
```

设置文本字符间距。取值小于0，字符聚集重叠，取值大于0且随着数值变大，字符间距越来越大，稀疏分布。string类型支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-letterSpacing(value: number | ResourceStr): SpanAttribute--><!--Device-SpanAttribute-letterSpacing(value: number | ResourceStr): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number \| ResourceStr | 是 | 文本字符间距。<br/>单位：[fp](../../../reference/apis-arkui/arkui-ts/ts-pixel-units.md#基本像素单位) <br>从API version 20开始，支持[Resource](../../apis-localization-kit/arkts-apis/arkts-localization-resource-resource-i.md)类型。<br>**起始版本：** 20 |

## lineHeight

```TypeScript
lineHeight(value: Length)
```

设置文本行高。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SpanAttribute-lineHeight(value: Length): SpanAttribute--><!--Device-SpanAttribute-lineHeight(value: Length): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 文本行高。 <br/> number类型时单位为fp。设置string类型时，支持number类型取值的字符串形式，可以附带单位，例如"10"、"10fp"。 |

## textCase

```TypeScript
textCase(value: TextCase)
```

设置文本大小写。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SpanAttribute-textCase(value: TextCase): SpanAttribute--><!--Device-SpanAttribute-textCase(value: TextCase): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [TextCase](../arkts-apis/arkts-arkui-textcase-e.md) | 是 | 文本大小写。<br/>默认值：TextCase.Normal |

## textShadow

```TypeScript
textShadow(value: ShadowOptions | Array<ShadowOptions>)
```

设置文字阴影效果。该接口支持以数组形式入参，实现多重文字阴影。不支持fill字段, 不支持智能取色模式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-SpanAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): SpanAttribute--><!--Device-SpanAttribute-textShadow(value: ShadowOptions | Array<ShadowOptions>): SpanAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [ShadowOptions](arkts-arkui-shadowoptions-i.md) \| Array&lt;ShadowOptions&gt; | 是 | 文字阴影效果。 |

