# SweepGradientOptions

角度渐变参数。

> **说明：**
>
> 为规范匿名对象的定义，API 18版本修改了此处的元素定义。其中，保留了历史匿名对象的起始版本信息，会出现外层元素@since版本号高于内层元素版本号的情况，但这不影响接口的使用。

> **说明：**
>
> metricsColors参数的约束：
>
> [ColorMetrics](../arkts-apis/arkts-arkui-colormetrics-c.md)表示填充的颜色，可以使用[colorWithSpace](../arkts-apis/arkts-arkui-colormetrics-c.md#colorwithspace-1)
> 方法构造指定色域属性的颜色。number表示指定颜色所处的位置，取值范围为[0, 1.0]，0表示需要设置渐变色的容器开始处，1.0表示容器的结束处。为了实现多个颜色渐变效果，多个数组中的number类型参数应递增设置。如果后一个
> 数组中的number类型参数小于前一个数组的number类型参数，将按照等于前一个数组number值处理。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## center

```TypeScript
center: [Length, Length]
```

Defines center point for angle gradient.

Anonymous Object Rectification.

**类型：** [Length, Length]

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## colors

```TypeScript
colors: Array<[ResourceColor, number]>
```

Defines color description for gradients.

Anonymous Object Rectification.

**类型：** Array<[ResourceColor, number]>

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## end

```TypeScript
end?: number | string
```

Defines end point of angle gradient.

Anonymous Object Rectification.

**类型：** number | string

**默认值：** 0

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## metricsColors

```TypeScript
metricsColors?: Array<[ColorMetrics, number]>
```

Defines color description in ColorMetrics format for gradients.
This parameter takes precedence over colors parameter.

**类型：** Array<[ColorMetrics, number]>

**起始版本：** 20

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本20开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## repeating

```TypeScript
repeating?: boolean
```

Defines gradient colors with repeated coloring.

Anonymous Object Rectification.

**类型：** boolean

**默认值：** false

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## rotation

```TypeScript
rotation?: number | string
```

Defines the rotation angle of the gradient.

Anonymous Object Rectification.

**类型：** number | string

**默认值：** 0

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## start

```TypeScript
start?: number | string
```

Defines the starting point of angle gradient.

Anonymous Object Rectification.

**类型：** number | string

**默认值：** 0

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本18开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

