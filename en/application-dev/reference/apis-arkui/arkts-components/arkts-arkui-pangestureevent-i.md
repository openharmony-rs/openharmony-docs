# PanGestureEvent

Inherits from [BaseGestureEvent](arkts-arkui-basegestureevent-i.md). This object can be passed as the **event** parameter of [onGestureJudgeBegin](arkts-arkui-commonmethod-c.md#ongesturejudgebegin).

**Inheritance/Implementation:** PanGestureEvent extends [BaseGestureEvent](arkts-arkui-basegestureevent-i.md)

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX: number
```

Offset of the gesture event on the x-axis relative to the original area of the current component, in vp. A positive value means to pan from left to right, and a negative value means the opposite.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY: number
```

Offset of the gesture event on the y-axis relative to the original area of the current component, in vp. A positive value means to pan from top to bottom, and a negative value means the opposite.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

Velocity along the main axis. The value is the arithmetic square root of the sum of squares of the velocity along the x- and y-axis. The unit is vp/s.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocityX

```TypeScript
velocityX: number
```

Velocity along the x-axis. The origin of the coordinate axis is the upper left corner of the screen. The velocity is positive if the movement is from left to right, and it is negative if the movement is from right to left. The unit is vp/s.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocityY

```TypeScript
velocityY: number
```

Velocity along the y-axis. The origin of the coordinate axis is the upper left corner of the screen. The velocity is positive if the movement is from top to bottom, and it is negative if the movement is from bottom to top. The unit is vp/s.

**Type:** number

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
