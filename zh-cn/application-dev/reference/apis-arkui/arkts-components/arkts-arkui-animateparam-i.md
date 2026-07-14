# AnimateParam

动画效果相关参数。

**起始版本：** 7

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## curve

```TypeScript
curve?: Curve | string | ICurve
```

动画曲线。

推荐以Curve或ICurve形式指定。

当类型为string时，为动画插值曲线，仅支持以下可选值：

"linear"：动画线性变化。

"ease"：动画开始和结束时的速度较慢，cubic-bezier(0.25、0.1、0.25、1.0)。

"ease-in"：动画播放速度先慢后快，cubic-bezier(0.42, 0.0, 1.0, 1.0)。

"ease-out"：动画播放速度先快后慢，cubic-bezier(0.0, 0.0, 0.58, 1.0)。

"ease-in-out"：动画播放速度先加速后减速，cubic-bezier(0.42, 0.0, 0.58, 1.0)。

"fast-out-slow-in"：标准曲线，cubic-bezier(0.4, 0.0, 0.2, 1.0)。

"linear-out-slow-in"：减速曲线，cubic-bezier(0.0, 0.0, 0.2, 1.0)。

"fast-out-linear-in"：加速曲线，cubic-bezier(0.4, 0.0, 1.0, 1.0)。

"friction"：阻尼曲线，cubic-bezier(0.2, 0.0, 0.2, 1.0)。

"extreme-deceleration"：急缓曲线，cubic-bezier(0.0, 0.0, 0.0, 1.0)。

"rhythm"：节奏曲线，cubic-bezier(0.7, 0.0, 0.2, 1.0)。

"sharp"：锐利曲线，cubic-bezier(0.33, 0.0, 0.67, 1.0)。

"smooth"：平滑曲线，cubic-bezier(0.4, 0.0, 0.4, 1.0)。

"cubic-bezier(x1, y1, x2, y2)"：三次贝塞尔曲线，x1、x2的值必须处于0-1之间。例如"cubic-bezier(0.42, 0.0, 0.58, 1.0)"。

"steps(number,step-position)"：阶梯曲线，number必须设置，为正整数，step-position参数可选，支持设置start或end，默认值为end。例如"steps(3,start)"。

"interpolating-spring(velocity,mass,stiffness,damping)"：具体参数含义参考插值弹簧曲线
[curves.interpolatingSpring](../arkts-apis/arkts-arkui-interpolatingspring-f.md#interpolatingspring-1)。

"responsive-spring-motion(response,dampingFraction,overlapDuration)"：具体参数含义参考弹性跟手动画曲线
[curves.responsiveSpringMotion](../arkts-apis/arkts-arkui-responsivespringmotion-f.md#responsivespringmotion-1)。

"spring(velocity,mass,stiffness,damping)"：具体参数含义参考弹簧曲线[curves.springCurve](../arkts-apis/arkts-arkui-springcurve-f.md#springcurve-1)。

"spring-motion(response,dampingFraction,overlapDuration)"：具体参数含义参考弹性动画曲线
[curves.springMotion](../arkts-apis/arkts-arkui-springmotion-f.md#springmotion-1)。

默认值：Curve.EaseInOut

**类型：** Curve | string | ICurve

**默认值：** Curve.EaseInOut

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

动画延迟播放时间，单位为ms(毫秒)，默认不延时播放。

默认值：0

取值范围：(-∞, +∞)

**说明**：1.delay>=0为延迟播放，delay<0表示提前播放。对于delay<0的情况：当delay的绝对值小于实际动画时长，动画将在开始后第一帧直接运动到delay绝对值的时刻的状态；当delay的绝对值大于等于实际
动画时长，动画将在开始后第一帧直接运动到终点状态。其中实际动画时长等于单次动画时长乘以动画播放次数。

2. 设置浮点型类型的值时，向下取整。例如，设置值为1.2，按照1处理。

**类型：** number

**默认值：** 0

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## duration

```TypeScript
duration?: number
```

动画持续时间，单位为毫秒。

默认值：1000

**说明**：1. API版本26.0.0之前，在ArkTS卡片上最大动画持续时间为1000毫秒，若超出则固定为1000毫秒。从API版本26.0.0开始，在ArkTS卡片上最大动画持续时间调整为2000毫秒。

2. 可以通过在持续时间为0的动画闭包函数中改变属性，以实现停止该属性动画的效果。
3. 设置小于0的值时按0处理。
4. 设置浮点型类型的值时，向下取整。例如，设置值为1.2，按照1处理。
5. curve配置[springMotion](../arkts-apis/arkts-arkui-springmotion-f.md#springmotion-1)、[responsiveSpringMotion](../arkts-apis/arkts-arkui-responsivespringmotion-f.md#responsivespringmotion-1)、[interpolatingSpring](../arkts-apis/arkts-arkui-interpolatingspring-f.md#interpolatingspring-1)曲线时，duration不生效。

**类型：** number

**默认值：** 1000

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expectedFrameRateRange

```TypeScript
expectedFrameRateRange?: ExpectedFrameRateRange
```

设置动画的期望帧率。

**类型：** ExpectedFrameRateRange

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## finishCallbackType

```TypeScript
finishCallbackType?: FinishCallbackType
```

在动画中定义onFinish回调的类型。

默认值：FinishCallbackType.REMOVED

**类型：** FinishCallbackType

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本11开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations?: number
```

动画播放次数。默认播放一次，设置为-1时表示无限次播放。设置为0时表示无动画效果。

默认值：1

取值范围：[-1, +∞)

**说明**：设置浮点型类型的值时，向下取整。例如，设置值为1.2，按照1处理。

**类型：** number

**默认值：** 1

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish?: () => void
```

动画播放完成回调。UIAbility从前台切换至后台时会立即结束仍在步进中的有限循环动画，触发播放完成回调。

在设置的开发者选项中关闭过渡动画，以及tempo设置为+∞时，动画播放完成回调会立即执行。

**类型：** () => void

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## playMode

```TypeScript
playMode?: PlayMode
```

动画播放模式，默认播放完成后从头开始播放。

默认值：PlayMode.Normal

相关使用约束请参考PlayMode说明。

> **PlayMode说明：**
>
> - PlayMode推荐使用PlayMode.Normal和PlayMode.Alternate，此场景下动画的第一轮是正向播放的。如使用PlayMode.Reverse和PlayMode.AlternateReverse，则动画
> 的第一轮是逆向播放的，在动画刚开始时会跳变到终止状态，然后逆向播放动画。
>
> - 使用PlayMode.Alternate或PlayMode.AlternateReverse时，开发者应保证动画最终状态和状态变量的取值一致，即应保证动画的最后一轮是正向播放的。使用PlayMode.Alternate时，
> iterations应为奇数。使用PlayMode.AlternateReverse时，iterations应为偶数。
>
> - 不推荐使用PlayMode.Reverse，此场景下不仅会导致动画刚开始就跳变到终止状态，也会导致动画最终状态和状态变量的取值不同。

**类型：** PlayMode

**默认值：** PlayMode.Normal

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本9开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## tempo

```TypeScript
tempo?: number
```

动画播放速度，值越大动画播放越快，值越小播放越慢，为0时无动画效果。

当设置为+∞时，动画会在当帧结束，动画结束回调会立即执行。

默认值：1.0

取值范围：[0, +∞)

**说明**：当设置小于0的值时按1处理。

**类型：** number

**默认值：** 1.0

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

