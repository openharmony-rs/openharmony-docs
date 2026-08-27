# Gauge属性/事件

除支持[通用属性](arkts-arkui-commonmethod-c.md)外，还支持以下属性。支持[通用事件](arkts-arkui-commonmethod-c.md)。

**继承/实现关系：** GaugeAttribute extends CommonMethod<GaugeAttribute>

**起始版本：** 8

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## 导入模块

```TypeScript
```

## colors

```TypeScript
colors(colors: ResourceColor | LinearGradient | Array<[ResourceColor | LinearGradient, number]>)
```

设置量规图的颜色。从API version 11开始，该接口使用以下规则：参数类型为[ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md)，则圆环类型为单色环。参数类型为LinearGradient，则圆环类型为渐变环。参数类型为数组，则圆环类型为分段渐变环，第一个参数为颜色值或渐变对象（LinearGradient），若设置为非颜色类型，则该颜色值置为"0xFFE84026"。第二个参数为颜色所占比重，若设置为负数或是非数值类型，则将比重置为 0。分段渐变环最大显示段数为9段，若多于9段，则多于部分不显示。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| colors | [ResourceColor](../arkts-apis/arkts-arkui-resourcecolor-t.md) \| LinearGradient \| Array & lt;[ResourceColor \ | LinearGradient, number] & gt; | 是 | 量规图的颜色，支持分段颜色设 置。 API version 9 默认值：Color.Black API version 11默认值： 若不传颜色，或者数组为空，无法确定圆环类型及颜色，则圆环颜色为"0xFF64BB5C"、"0xFFF7CE00"、"0xFFE84026"的渐变环。 若传入颜色，但颜色值有误，则该颜色为"0xFFE84026"。 若对应颜色的比重为0，则该颜色在圆环中不显示。若所有颜色比重均为0，圆环不显示。 从API version 10开始，支持Array & lt;ResourceColor, number & gt;类型。 从API version 11开始，新增支持LinearGradient和Array & lt;LinearGradient, number & gt;类型。<br>**起始版本：** 11 |

## contentModifier

```TypeScript
contentModifier(modifier: ContentModifier<GaugeConfiguration>)
```

定制Gauge内容区的方法。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| modifier | [ContentModifier](arkts-arkui-contentmodifier-i.md)&lt;[GaugeConfiguration](arkts-arkui-gaugeconfiguration-i.md)&gt; | 是 | 在Gauge组件上定制内容区的方法。 modifier：内容修改器，开发者需要自定义class实现ContentModifier接口。 |

## description

```TypeScript
description(value: CustomBuilder)
```

设置说明内容。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [CustomBuilder](arkts-arkui-custombuilder-t.md) | 是 | 说明内容。    **说明：** @Builder中的内容由开发者自定义，建议使用文本或者图片。 若自定义部分的宽高为百分比形式，则基准范围为圆环直径的44.4%*25.4%的矩形（图片为28.6%*28.6%），距离圆环底部0vp，左右居中。 设置null则不显示内容。 不设置则依赖是否设置数据最大最小值。 若设置最大最小值或者只设置其中一个，则显示最大最小值。 若未设置最大最小值，则不显示内容。 最大最小值显示在圆环底部，位置不可移动，若圆环开口角度设置不恰当，存在圆环遮挡文字的情况。 |

## endAngle

```TypeScript
endAngle(angle: number)
```

设置终止角度位置。起始角度和终止角度的差值过小时，会绘制出异常图像，请取合理的起始角度和终止角度。建议使用单色环改变Gauge的value参数实现数据值的调节，可通过定时器setTimeout进行数值的延迟加载。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | 终止角度位置，时钟0点为0度，顺时针方向为正角度，逆时针方向为负角度，超过360度等价于对360度取余后的角度。 默认值：360 单位：deg（度） 从起始位置到终止位置的绘制只有顺时针方向。 起始角度和终止角度的差值过小时，会绘制出异常图像，请取合理的起始角度和终止角度。 |

## indicator

```TypeScript
indicator(value: GaugeIndicatorOptions)
```

设置指针样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GaugeIndicatorOptions](arkts-arkui-gaugeindicatoroptions-i.md) | 是 | 指针样式。    **说明：** 设置null则不显示指针。 |

## privacySensitive

```TypeScript
privacySensitive(isPrivacySensitiveMode: Optional<boolean>)
```

设置隐私敏感。

> **说明：**
> 
> 从API version 20开始，该接口支持在attributeModifier中调用。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本12开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| isPrivacySensitiveMode | [Optional](arkts-arkui-optional-t.md)&lt;boolean&gt; | 是 | 设置隐私敏感。在隐私模式下，Gauge指针指向0位置，最大值最小值文本将被遮罩，量程显示灰色或底色。true表示打开隐私敏 感，false表示关闭隐私敏感。    **说明：** 设置null则不敏感。<!--Del--> 需要在卡片中使用Progress，并用FormComponent组件设置[隐私遮罩](arkts-arkui-commonmethod-c.md#obscured)属性，显示卡片时才有 隐私遮罩效果。<!--DelEnd--> |

## startAngle

```TypeScript
startAngle(angle: number)
```

设置起始角度位置。起始角度和终止角度的差值过小时，会绘制出异常图像，请取合理的起始角度和终止角度。建议使用单色环改变Gauge的value参数实现数据值的调节，可通过定时器setTimeout进行数值的延迟加载。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| angle | number | 是 | 起始角度位置，时钟0点为0度，顺时针方向为正角度，逆时针方向为负角度，超过360度等价于对360度取余后的角度。 默认值：0 单位：deg（度） 从起始位置到终止位置的绘制只有顺时针方向。 起始角度和终止角度的差值过小时，会绘制出异常图像，请取合理的起始角度和终止角度。 |

## strokeWidth

```TypeScript
strokeWidth(length: Length)
```

设置环形量规图的环形厚度。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| length | [Length](../arkts-apis/arkts-arkui-length-t.md) | 是 | 环形量规图的环形厚度。 默认值：4 单位：vp    **说明：** 设置小于等于0的值时，按默认值显示。 环形厚度的最大值为圆环的半径，超过最大值按最大值处理。 不支持百分比。 |

## trackShadow

```TypeScript
trackShadow(value: GaugeShadowOptions)
```

设置阴影样式。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本23开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | [GaugeShadowOptions](arkts-arkui-gaugeshadowoptions-i.md) | 是 | 添加阴影效果，可以指定模糊半径、X轴和Y轴的偏移量。    **说明：** 阴影颜色与圆环颜色一致。 设置null为不开启投影。 |

## value

```TypeScript
value(value: number)
```

设置量规图的数据值。

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | number | 是 | 量规图的数据值，可用于动态修改量规图的数据值。    **说明：** value不在min和max范围内时使用min作为默认值。 默认值：0 |
