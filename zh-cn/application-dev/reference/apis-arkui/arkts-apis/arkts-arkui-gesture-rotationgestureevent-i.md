# RotationGestureEvent

继承自[BaseGestureEvent](arkts-arkui-gesture-basegestureevent-i.md#BaseGestureEvent)。可将该对象作为onGestureJudgeBegin的 event参数来传递。

**继承/实现关系：** RotationGestureEvent extends [BaseGestureEvent](arkts-arkui-gesture-basegestureevent-i.md#BaseGestureEvent)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-export interface RotationGestureEvent--><!--Device-unnamed-export interface RotationGestureEvent-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: double
```

表示旋转角度，单位为deg。 **说明：** 角度计算方式：当滑动手势被识别后，连接两根手指之间的线被识别为起始线条。随着手指的滑动，手指之间的线条会发生旋转。根据起始线条和当前线条两端点的坐标，使用反正切函数分别计算其相对于水平方向的夹角。 最终的旋转角度为：arctan2(cy2-cy1, cx2-cx1) - arctan2(y2-y1, x2-x1) 在起始线条为坐标系的情况下，顺时针旋转为0到180度，逆时针旋转为0到-180度。

**类型：** double

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-RotationGestureEvent-angle: double--><!--Device-RotationGestureEvent-angle: double-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

