# SwipeGestureHandlerOptions

```TypeScript
interface SwipeGestureHandlerOptions extends BaseHandlerOptions
```

Provides the parameters of the swipe gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md).

**Inheritance/Implementation:** SwipeGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)

**Since:** 12

<!--Device-unnamed-interface SwipeGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface SwipeGestureHandlerOptions extends BaseHandlerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## direction

```TypeScript
direction?: SwipeDirection
```

Swipe direction that triggers the swipe gesture. **SwipeDirection.All** applies to scenarios where a swipe in any direction can trigger the action; **SwipeDirection.Horizontal** applies to scenarios where only horizontal swipes are responded to, such as page turning or carousel switching; **SwipeDirection.Vertical** applies to scenarios where only vertical swipes are responded to, such as switching content up and down; **SwipeDirection.None** applies to scenarios where the swipe gesture is not triggered for the time being.

Default value: **SwipeDirection.All**

**Type:** [SwipeDirection](arkts-arkui-tapgesture-comp-swipedirection-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeGestureHandlerOptions-direction?: SwipeDirection--><!--Device-SwipeGestureHandlerOptions-direction?: SwipeDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Minimum number of fingers required to trigger a swipe. Value range: [1, 10]. If the value is out of range, the default value is used. Set this parameter to 1 when a single-finger swipe is sufficient to trigger the action; set it to a value from 2 to 10 when you need to reduce accidental touches and require multi-finger coordination to trigger the swipe.

Default value: **1**

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeGestureHandlerOptions-fingers?: number--><!--Device-SwipeGestureHandlerOptions-fingers?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## speed

```TypeScript
speed?: number
```

Minimum speed for recognizing a swipe. Set a smaller positive threshold when you need to recognize swipes more sensitively; set a larger threshold when you need to reduce the chance of ordinary pans being misrecognized as swipes. It is recommended to use the default value first and then adjust it based on interaction sensitivity and accidental touch conditions.

Default value: 100 vp/s

Value range: (0, +∞), unit: vp/s

**NOTE:** 

If the value is less than or equal to 0, it will be converted to the default value.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeGestureHandlerOptions-speed?: number--><!--Device-SwipeGestureHandlerOptions-speed?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
