# BadgeStyle

Badge的样式。包括文本颜色、尺寸、字重、圆点颜色和尺寸等。

> **说明：**  
>  
> - 当`borderWidth`大于0且`borderColor`与`badgeColor`颜色不一致时，先绘制角标，再绘制描边。由于边缘像素经过抗锯齿处理，抗锯齿产生半透明像素，四角会出现 `badgeColor` 颜色的描边  
> 线。如需实现相关场景，建议使用[Text](../../apis-arkgraphics2d/arkts-apis/arkts-graphics-text.md)组件设置[outline](arkts-arkui-commonmethod-c.md#outline-1)代替Badge组件。

**起始版本：** 7

<!--Device-unnamed-declare interface BadgeStyle--><!--Device-unnamed-declare interface BadgeStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## badgeColor

```TypeScript
badgeColor?: ResourceColor
```

Badge的颜色。

默认值：Color.Red

**类型：** ResourceColor

**默认值：** Color.Red

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeStyle-badgeColor?: ResourceColor--><!--Device-BadgeStyle-badgeColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## badgeSize

```TypeScript
badgeSize?: number | ResourceStr
```

Badge的大小。string类型仅支持number类型取值的字符串形式，可以附带单位，支持的单位有"px"、"vp"、"fp"、"lpx"，例如"16"、"16fp"，不附带单位时默认单位为"fp"。

默认值：16vp

默认单位：fp

取值范围：大于0；取值为0时不显示Badge，取值小于0时取默认值。

**说明：**

1. 不支持设置百分比，当设置为百分比时，按照默认值处理。2. 从API version 20开始，支持ResourceStr类型。3. 当设置了fontSize且badgeSize小于fontSize时，badgeSize将按照fontSize生效。

**类型：** number \| ResourceStr

**默认值：** 16vp

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeStyle-badgeSize?: number | ResourceStr--><!--Device-BadgeStyle-badgeSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderColor

```TypeScript
borderColor?: ResourceColor
```

底板描边颜色。

默认值：Color.Red

**类型：** ResourceColor

**默认值：** Color.Red

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BadgeStyle-borderColor?: ResourceColor--><!--Device-BadgeStyle-borderColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## borderWidth

```TypeScript
borderWidth?: Length
```

底板描边粗细。

默认值：1

单位：vp

**说明：**

不支持设置百分比，当设置为百分比时，按照默认值处理。

**类型：** Length

**默认值：** 1vp

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BadgeStyle-borderWidth?: Length--><!--Device-BadgeStyle-borderWidth?: Length-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## color

```TypeScript
color?: ResourceColor
```

文本颜色。

默认值：Color.White

**类型：** ResourceColor

**默认值：** Color.White

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeStyle-color?: ResourceColor--><!--Device-BadgeStyle-color?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## enableAutoAvoidance

```TypeScript
enableAutoAvoidance?: boolean
```

增加角标文本延伸显示时是否避让。

true表示避让，false表示不避让。

默认值：false

**说明：**

1. 避让效果为角标文本向组件内部延伸显示。2. 当外描边的宽度大于0时，角标的延伸起点为外描边的内侧。3. 当position设置为具体坐标值时，角标不进行避让处理。

**类型：** boolean

**默认值：** false

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-BadgeStyle-enableAutoAvoidance?: boolean--><!--Device-BadgeStyle-enableAutoAvoidance?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontSize

```TypeScript
fontSize?: number | ResourceStr
```

文本大小。string类型仅支持number类型取值的字符串形式，可以附带单位，支持的单位有"px"、"vp"、"fp"、"lpx"，例如"10"、"10fp"，不附带单位时默认单位为"fp"。

默认值：10vp

默认单位：fp

取值范围：大于0；取值为0时不显示文本，取值小于0时取默认值。

**说明：**

1. 不支持设置百分比，当设置为百分比时，按照默认值处理。2. 从API version 20开始，支持ResourceStr类型。

**类型：** number \| ResourceStr

**默认值：** 10vp

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-BadgeStyle-fontSize?: number | ResourceStr--><!--Device-BadgeStyle-fontSize?: number | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## fontWeight

```TypeScript
fontWeight?: number | FontWeight | ResourceStr
```

设置文本的字体粗细。number类型取值范围：[100, 900]，取值间隔为100。取值越大，字体越粗。设置number类型在取值范围外时，按默认值400处理。string类型仅支持number类型取值的字符串形式，例如"400"，以及"bold"、"bolder"、"lighter"、"regular"、"medium"，分别对应FontWeight中相应的枚举值。

默认值：FontWeight.Normal

**说明：**

不支持设置百分比，当设置为百分比时，按照默认值处理。从API version 20开始，支持ResourceStr类型。

**类型：** number \| FontWeight \| ResourceStr

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-BadgeStyle-fontWeight?: number | FontWeight | ResourceStr--><!--Device-BadgeStyle-fontWeight?: number | FontWeight | ResourceStr-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outerBorderColor

```TypeScript
outerBorderColor?: ResourceColor
```

底板外描边颜色。

默认值：Color.White

**类型：** ResourceColor

**默认值：** Color.White

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-BadgeStyle-outerBorderColor?: ResourceColor--><!--Device-BadgeStyle-outerBorderColor?: ResourceColor-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## outerBorderWidth

```TypeScript
outerBorderWidth?: LengthMetrics
```

底板外描边粗细。

默认值：0

单位：vp

不支持设置百分比，当设置为百分比时，按照默认值处理。

**类型：** LengthMetrics

**默认值：** 0vp

**起始版本：** 22

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本22开始，该接口支持在原子化服务API中使用。

<!--Device-BadgeStyle-outerBorderWidth?: LengthMetrics--><!--Device-BadgeStyle-outerBorderWidth?: LengthMetrics-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

