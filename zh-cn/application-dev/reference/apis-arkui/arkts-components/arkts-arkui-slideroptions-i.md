# SliderOptions

滑动条的信息。

**起始版本：** 7

<!--Device-unnamed-declare interface SliderOptions--><!--Device-unnamed-declare interface SliderOptions-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: Axis
```

设置滑动条滑动方向为水平或竖直方向。

默认值：Axis.Horizontal

**类型：** Axis

**默认值：** Axis.Horizontal [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-direction?: Axis--><!--Device-SliderOptions-direction?: Axis-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## max

```TypeScript
max?: number
```

设置最大值。

默认值：100

**说明：**

min >= max异常情况，min取默认值0，max取默认值100。

value不在[min, max]范围之内，取min或者max，靠近min取min，靠近max取max。

**类型：** number

**默认值：** 100 [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-max?: number--><!--Device-SliderOptions-max?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## min

```TypeScript
min?: number
```

设置最小值。

默认值：0

**类型：** number

**默认值：** 0 [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-min?: number--><!--Device-SliderOptions-min?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## reverse

```TypeScript
reverse?: boolean
```

设置滑动条取值范围是否反向。

true：横向Slider从右往左滑动，竖向Slider从下往上滑动；false：横向Slider从左往右滑动，竖向Slider从上往下滑动。

默认值：false

**类型：** boolean

**默认值：** false [since 11]

**起始版本：** 8

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-reverse?: boolean--><!--Device-SliderOptions-reverse?: boolean-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## step

```TypeScript
step?: number
```

设置Slider滑动步长。

默认值：1

取值范围：[0.01, max - min]

**说明：**

若设置的step值小于0或大于max值，则按默认值显示。

**类型：** number

**默认值：** 1 - Value range: [0.01, max - min] [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-step?: number--><!--Device-SliderOptions-step?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## style

```TypeScript
style?: SliderStyle
```

设置Slider的滑块与滑轨显示样式。

默认值：SliderStyle.OutSet

**类型：** SliderStyle

**默认值：** SliderStyle.OutSet [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-style?: SliderStyle--><!--Device-SliderOptions-style?: SliderStyle-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## value

```TypeScript
value?: number
```

当前进度值。

默认值：与属性min的取值一致。

从API version 10开始，该属性支持[$$](../../../ui/state-management/arkts-two-way-sync.md)双向绑定变量。

该属性支持[!!](../../../ui/state-management/arkts-new-binding.md#系统组件参数双向绑定)双向绑定变量。

取值范围： [min, max]

小于min时取min，大于max时取max。

$$运算符为系统组件提供TS变量的引用，使得TS变量和slider组件的value值保持同步。详细使用示例请参考[示例7（设置滑动条的双向绑定）](../../../reference/apis-arkui/arkui-ts/ts-basic-components-slider.md#示例7设置滑动条的双向绑定)。

**类型：** number

**默认值：** same as the value of min [since 11]

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

<!--Device-SliderOptions-value?: number--><!--Device-SliderOptions-value?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

