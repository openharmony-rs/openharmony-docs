# RotationGestureEvent

Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin).

**Inheritance/Implementation:** RotationGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number
```

Rotation angle, in deg.

**NOTE:** 

Angle calculation: When a rotation gesture is detected, the line connecting the two fingers is identified as the starting line. As the fingers slide, the line between them rotates. Based on the coordinates of the end points of the starting line and the current line, the arctangent function is used to calculate the included angles relative to the horizontal direction.

The final rotation angle is: arctan2(cy2 - cy1, cx2 - cx1) - arctan2(y2 - y1, x2 - x1)

With the starting line as the reference axis, clockwise rotation ranges from 0 to 180 degrees, and counterclockwise rotation ranges from 0 to –180 degrees.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
