# SwipeGestureEvent

继承自[BaseGestureEvent](arkts-arkui-basegestureevent-i.md)。可将该对象作为[onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin-1)的
event参数来传递。

**继承/实现关系：** SwipeGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**起始版本：** 11

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number
```

表示快滑手势的角度，即手指滑动的瞬时方向与水平正方向的夹角，单位为deg。

**说明：**

以水平正方向为基准，滑动方向位于水平正方向顺时针侧时，角度范围为0到180度；位于水平正方向逆时针侧时，角度范围为0到-180度。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: number
```

快滑手势速度，即所有手指相对当前组件元素原始区域滑动的平均速度，单位为vp/s。

**类型：** number

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

