# KeyframeAnimateParam

动画选项设置。

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## delay

```TypeScript
delay?: number
```

动画的整体延时时间，单位为ms（毫秒），默认不延时播放。

默认值：0

**说明：**

delay>=0为延迟播放，delay<0表示提前播放。对于delay<0的情况：当delay的绝对值小于实际动画时长，动画将在开始后第一帧直接运动到delay绝对值的时刻的状态；当delay的绝对值大于等于实际动画时长，动画将
在开始后第一帧直接运动到终点状态。其中实际动画时长等于单次动画时长乘以动画播放次数。

**类型：** number

**默认值：** 0

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## expectedFrameRateRange

```TypeScript
expectedFrameRateRange?: ExpectedFrameRateRange
```

设置动画的期望帧率。

**默认值：**{min:0, max:0, expected:0}，即跟随应用帧率。

**说明：**

开发者通过设置有效的期望帧率后，系统会收集设置的请求帧率，进行决策和分发，在渲染管线上进行分频，尽量能够满足开发者的期望帧率。开发者设置的期望帧率值不能代表最终实际效果，会受限于系统能力和屏幕刷新率。

**类型：** ExpectedFrameRateRange

**默认值：** { min: 0, expected: 0, max: 0 }

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本19开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## iterations

```TypeScript
iterations?: number
```

动画播放次数。默认播放一次，设置为-1时表示无限次播放。设置为0时表示无动画效果。

默认值：1

**取值范围：**[-1, +∞)

**说明：**

- 设置浮点型类型的值时，向下取整。例如，设置值为1.2，按照1处理。

**类型：** number

**默认值：** 1

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## onFinish

```TypeScript
onFinish?: () => void
```

动画播放完成回调。当keyframe动画所有次数播放完成后调用。在设置的开发者选项中关闭过渡动画，或UIAbility从前台切换至后台时会立即结束仍在播放中的有限循环keyframe动画，触发播放完成回调。

**类型：** () => void

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

