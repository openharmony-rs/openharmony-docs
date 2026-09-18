# SwipeGestureEvent

Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin).

**Inheritance/Implementation:** SwipeGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number
```

Angle of the swipe gesture, that is, the angle between the instantaneous direction of finger sliding and the positive horizontal direction. The unit is deg.

**NOTE:** 

With the positive horizontal direction as the reference, when the sliding direction is on the clockwise side of the positive horizontal direction, the angle ranges from 0 to 180 degrees; when on the counterclockwise side, the angle ranges from 0 to –180 degrees.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: number
```

Swipe gesture speed, defined as the average swipe speed of all fingers relative to the original area of the current component. The unit is vp/s.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
