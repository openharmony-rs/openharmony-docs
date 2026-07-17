# KeyframeState

设置关键帧选项。

**起始版本：** 11

<!--Device-unnamed-declare interface KeyframeState--><!--Device-unnamed-declare interface KeyframeState-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

该关键帧使用的动画曲线。

推荐以Curve或ICurve形式指定。

当类型为string时，为动画插值曲线，取值参考[AnimateParam](../../../../reference/apis-arkui/arkui-ts/ts-explicit-animation.md#animateparam对象说明)的curve参数。

默认值：Curve.EaseInOut

**说明：**

由于[springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md#springmotion-1)、[responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md#responsivespringmotion-1)、[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md#interpolatingspring-1)曲线时长不生效，故不支持这三种曲线。

**类型：** Curve | string | ICurve

**默认值：** Curve.EaseInOut

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyframeState-curve?: Curve | string | ICurve--><!--Device-KeyframeState-curve?: Curve | string | ICurve-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: number
```

该段关键帧动画的持续时间，单位为毫秒。

取值范围：[0, +∞)

**说明：**

- 设置小于0的值时按0处理。

- 设置浮点型的值时，向下取整。例如，设置值为1.2，按照1处理。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyframeState-duration: number--><!--Device-KeyframeState-duration: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: () => void
```

指定在该关键帧时刻状态的闭包函数，即在该关键帧时刻要达到的状态。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-KeyframeState-event: () => void--><!--Device-KeyframeState-event: () => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

