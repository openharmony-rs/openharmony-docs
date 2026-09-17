# SwipeGestureHandlerOptions

Provides the parameters of the swipe gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md).

**Inheritance/Implementation:** SwipeGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: SwipeDirection
```

Directions in which the swipe gesture can be recognized.

Default value: **SwipeDirection.All**

**Type:** [SwipeDirection](arkts-arkui-swipedirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers to trigger a swipe gesture. The value ranges from 1 to 10.

Default value: **1**

Value range: [1, 10]

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed?: number
```

Minimum speed of the swipe gesture.

Default value: 100 vp/s

**NOTE:** 

If the value is less than or equal to 0, it will be converted to the default value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
