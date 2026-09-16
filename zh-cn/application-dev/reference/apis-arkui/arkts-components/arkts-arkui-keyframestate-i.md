# KeyframeState

关键帧状态设置。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## event

```TypeScript
event: () => void
```

设置该关键帧时刻目标状态的闭包函数，在该闭包中定义组件属性要达到的目标值。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

该关键帧使用的动画曲线。

推荐以Curve或ICurve形式指定。

当类型为string时，为动画插值曲线，取值参考[AnimateParam](arkts-arkui-animateparam-i.md)的curve参数，有效取值为“ linear”、“ease”、“ease-in”、“ease-out”、“ease-in-out”、“fast-out-slow-in”、“linear-out-slow-in”、“fast-out-linear-in”、“ friction”、“extreme-deceleration”、“rhythm”、“sharp”、“smooth”，以及“cubic-bezier(x1,y1,x2,y2)”、“steps(number,step- position)”格式字符串，不支持“springMotion”、“responsiveSpringMotion”、“interpolatingSpring”。

默认值：Curve.EaseInOut

**说明：** 

由于[springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md)、[responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md)、[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md)曲线时长不生效，故不支持这三种曲线。设置不支持的曲线时，使用默认曲线Curve.EaseInOut。

**类型：** [Curve](../arkts-apis/arkts-arkui-curve-e.md) &#124; string &#124; [ICurve](arkts-arkui-icurve-i.md)

**默认值：** Curve.EaseInOut

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration: number
```

该段关键帧动画的持续时间，单位为ms（毫秒）。

取值范围：[0, +∞)

**说明：** 

- 设置小于0的值时按0处理。  
- 设置浮点型的值时，截断取整。例如，设置值为1.2，按照1处理。  
- duration为0时，表示瞬时过渡到该关键帧状态，无动画过程。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full
