# TapGestureHandlerOptions

```TypeScript
interface TapGestureHandlerOptions extends BaseHandlerOptions
```

Provides the parameters of the tap gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md).

**Inheritance/Implementation:** TapGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-tapgesture-comp-basehandleroptions-i.md)

**Since:** 12

<!--Device-unnamed-interface TapGestureHandlerOptions extends BaseHandlerOptions--><!--Device-unnamed-interface TapGestureHandlerOptions extends BaseHandlerOptions-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## count

```TypeScript
count?: number
```

Number of consecutive taps. If the value is less than 1 or is not set, the default value is used.

Default value: **1**

Value range: [0, +∞)

**NOTE:** 

1. If multi-tap is configured, the timeout interval between a lift and the next tap is 300 ms.
2. If the distance between the last tapped position and the current tapped position exceeds 60 vp, gesture
recognition fails.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TapGestureHandlerOptions-count?: number--><!--Device-TapGestureHandlerOptions-count?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distanceThreshold

```TypeScript
distanceThreshold?: number
```

Movement threshold for the tap gesture. If the value is less than or equal to 0 or is not set, the default value is used.

Default value: **2^31-1**

Unit: vp

Value range: (0, +∞)

**NOTE:** 

If the finger movement exceeds the preset movement threshold, the gesture recognition fails. If the default threshold is used during initialization and the finger moves beyond the component's touch target, the tap gesture recognition fails.

**Type:** number

**Default:** Infinity

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-TapGestureHandlerOptions-distanceThreshold?: number--><!--Device-TapGestureHandlerOptions-distanceThreshold?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Number of fingers that trigger a tap. The minimum is 1 finger, and the maximum is 10 fingers. If the value is less than 1 or is not set, the default value is used.

Default value: **1**

**NOTE:** 

1. When multiple fingers are configured, if a sufficient number of fingers are not pressed within 300 ms after the
first finger is pressed, gesture recognition fails. If a sufficient number of fingers are not lifted within 300 ms after the first finger is lifted, gesture recognition fails.
2. When **isFingerCountLimited** is not enabled, if the actual number of tapping fingers exceeds the configured
value, gesture recognition succeeds. When **isFingerCountLimited** is enabled, the number of fingers touching the screen must be equal to the configured value; otherwise, gesture recognition fails.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-TapGestureHandlerOptions-fingers?: number--><!--Device-TapGestureHandlerOptions-fingers?: number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
