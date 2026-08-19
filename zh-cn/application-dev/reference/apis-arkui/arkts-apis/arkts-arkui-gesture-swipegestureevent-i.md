# SwipeGestureEvent

继承自[BaseGestureEvent](arkts-arkui-gesture-basegestureevent-i.md)。可将该对象作为onGestureJudgeBegin的 event参数来传递。

**继承/实现关系：** SwipeGestureEvent extends [BaseGestureEvent](arkts-arkui-gesture-basegestureevent-i.md)

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export interface SwipeGestureEvent--><!--Device-unnamed-export interface SwipeGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: double
```

表示快滑手势的角度，即手指滑动的瞬时方向与水平正方向的夹角，单位为deg。 **说明：** 以水平正方向为基准，滑动方向位于水平正方向顺时针侧时，角度范围为0到180度；位于水平正方向逆时针侧时，角度范围为0到-180度。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGestureEvent-angle: double--><!--Device-SwipeGestureEvent-angle: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: double
```

快滑手势速度，即所有手指相对当前组件元素原始区域滑动的平均速度，单位为vp/s。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwipeGestureEvent-speed: double--><!--Device-SwipeGestureEvent-speed: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

