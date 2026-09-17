# GestureEvent

Defines the gesture event information. Inherits from [BaseEvent](arkts-arkui-baseevent-i.md).

**Inheritance/Implementation:** GestureEvent extends [BaseEvent](arkts-arkui-baseevent-i.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## angle

```TypeScript
angle: number
```

Rotation angle for the **RotationGesture** event, in deg.

Angle of the swipe gesture for the **SwipeGesture** event, that is, the angle between the instantaneous direction of finger sliding and the positive horizontal direction, in deg.

**NOTE:** 

Rotation gesture angle calculation: When a rotation gesture is detected, the line connecting the two fingers is identified as the starting line. As the fingers slide, the line between them rotates. Based on the coordinates of the end points of the starting line and the current line, the arctangent function is used to calculate the included angles relative to the horizontal direction. The rotation angle is calculated as arctan2(cy2-cy1, cx2-cx1) - arctan 2(y2-y1, x2-x1). With the starting line as the reference axis, clockwise rotation ranges from 0 to 180 degrees, and counterclockwise rotation ranges from 0 to –180 degrees.

Value range: [-180, 180]

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingerInfos

```TypeScript
fingerInfos?: FingerInfo[]
```

Information about touch points of the gesture event. For gesture events initiated by a touchscreen, **fingerInfos** includes information about all touch points. For gesture events initiated by a mouse or touchpad, **fingerInfos** contains only one touch point.

**NOTE:** 

**fingerInfos** only records information about effective fingers that participate in the touch. Fingers that are pressed first but do not participate in triggering of the current gesture will not be shown in **fingerInfos**. The default value is an empty array **[]**, and an empty array indicates no effective touch point information.

**Type:** [FingerInfo](arkts-arkui-fingerinfo-i.md)[]

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingerList

```TypeScript
fingerList: FingerInfo[]
```

List of touch points of the gesture event. If the event input device is touchscreen, the list includes all touch points. If the event input device is mouse or touchpad, the list contains only one touch point.

**NOTE:** 

1. The index of a finger corresponds to its position, that is, the ID of a finger in **fingerList[index]** refers
to its index. If a finger is pressed first and does not participate in triggering of the current gesture, its position in **fingerList** is left empty.
2. **fingerList** is empty when gestures are triggered using a keyboard or game controller and no finger
information exists.

**Type:** [FingerInfo](arkts-arkui-fingerinfo-i.md)[]

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetX

```TypeScript
offsetX: number
```

X-axis offset of the gesture event relative to the finger press position, in vp. Used in **PanGesture** scenarios. A positive value means to pan from left to right, and a negative value means the opposite.

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## offsetY

```TypeScript
offsetY: number
```

Y-axis offset of the gesture event relative to the finger press position, in vp. Used in **PanGesture** scenarios. A positive value means to pan from top to bottom, and a negative value means the opposite.

Value range: (-∞, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pinchCenterX

```TypeScript
pinchCenterX: number
```

X-coordinate of the center of the pinch gesture, in vp, relative to the original area of the current component. This attribute is used for the **PinchGesture** event.

Value range: [0, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## pinchCenterY

```TypeScript
pinchCenterY: number
```

Y-coordinate of the center of the pinch gesture, in vp, relative to the original area of the current component. This attribute is used for the **PinchGesture** event.

Value range: [0, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## repeat

```TypeScript
repeat: boolean
```

Whether the event is a repeated trigger event, used in the **LongPressGesture** scenarios. The value **true** means that the event is a repeated trigger event, and **false** means the opposite.

**Type:** boolean

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## scale

```TypeScript
scale: number
```

Scale ratio. This attribute is used for the pinch gesture.

Value range: [0, +∞)

**Type:** number

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed: number
```

Swipe gesture speed, that is, the average swipe speed of all fingers relative to the original area of the current component, in vp/s. Used for the **SwipeGesture** event.

Value range: [0, +∞)

**Type:** number

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## tapLocation

```TypeScript
tapLocation?: EventLocationInfo
```

Coordinate information of the current tap gesture. For non-tap gestures, the return value of **tapLocation** is **undefined**.

**Type:** [EventLocationInfo](arkts-arkui-eventlocationinfo-i.md)

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocity

```TypeScript
velocity: number
```

Velocity along the main axis. This parameter is used in [PanGesture](arkts-arkui-tapgesture-comp-con.md#pangesture). The value is the arithmetic square root of the sum of squares of the velocity along the x- and y-axis. The unit is vp/s.

Value range: [0, +∞)

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocityX

```TypeScript
velocityX: number
```

Velocity along the x-axis. This parameter is used in [PanGesture](arkts-arkui-tapgesture-comp-con.md#pangesture). The origin of the coordinate axis is the upper left corner of the screen. The velocity is positive if the movement is from left to right, and it is negative if the movement is from right to left. The unit is vp/s.

Value range: (-∞, +∞)

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## velocityY

```TypeScript
velocityY: number
```

Velocity along the y-axis. This parameter is used in [PanGesture](arkts-arkui-tapgesture-comp-con.md#pangesture). The origin of the coordinate axis is the upper left corner of the screen. The velocity is positive if the movement is from top to bottom, and it is negative if the movement is from bottom to top. The unit is vp/s.

Value range: (-∞, +∞)

**Type:** number

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
