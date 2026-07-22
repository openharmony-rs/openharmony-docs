# PanGestureEvent

继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](../arkts-components/arkts-arkui-commonmethod-c.md#ongesturejudgebegin)的event参数来传递。

**继承/实现关系：** PanGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**起始版本：** 11

<!--Device-unnamed-interface PanGestureEvent extends BaseGestureEvent--><!--Device-unnamed-interface PanGestureEvent extends BaseGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX: number
```

手势事件x轴相对当前组件元素原始区域的偏移量，单位为vp，从左向右滑动offsetX为正，反之为负。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureEvent-offsetX: number--><!--Device-PanGestureEvent-offsetX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY: number
```

手势事件y轴相对当前组件元素原始区域的偏移量，单位为vp，从上向下滑动offsetY为正，反之为负。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureEvent-offsetY: number--><!--Device-PanGestureEvent-offsetY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

获取当前的主方向速度。为xy轴方向速度的平方和的算术平方根。单位为vp/s。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureEvent-velocity: number--><!--Device-PanGestureEvent-velocity: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocityX

```TypeScript
velocityX: number
```

获取当前手势的x轴方向速度。坐标轴原点为屏幕左上角，分正负方向速度，从左往右为正，反之为负。单位为vp/s。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureEvent-velocityX: number--><!--Device-PanGestureEvent-velocityX: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## velocityY

```TypeScript
velocityY: number
```

获取当前手势的y轴方向速度。坐标轴原点为屏幕左上角，分正负方向速度，从上往下为正，反之为负。单位为vp/s。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-PanGestureEvent-velocityY: number--><!--Device-PanGestureEvent-velocityY: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

