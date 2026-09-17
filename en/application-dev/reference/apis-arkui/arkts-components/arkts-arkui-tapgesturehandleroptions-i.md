# TapGestureHandlerOptions

Provides the parameters of the tap gesture handler. Inherits from [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md).

**Inheritance/Implementation:** TapGestureHandlerOptions extends [BaseHandlerOptions](arkts-arkui-basehandleroptions-i.md)

**Since:** 12

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## distanceThreshold

```TypeScript
distanceThreshold?: number
```

Movement threshold for the tap gesture. If the value is less than or equal to 0 or is not set, the default value is used.

Default value: **2^31-1**

Unit: vp

**NOTE:** 

If the finger movement exceeds the preset movement threshold, the gesture recognition fails. If the default threshold is used during initialization and the finger moves beyond the component's touch target, the tap gesture recognition fails.

**Type:** number

**Default:** Infinity

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## fingers

```TypeScript
fingers?: number
```

Number of fingers required to trigger a tap. The value ranges from 1 to 10. If the value is less than 1 or is not set, the default value is used.

Default value: **1**

**NOTE:** 

1. If the value is greater than 1, the tap gesture will fail to be recognized when the required number of fingers
is not pressed within 300 milliseconds after the first finger touches down, or when the required number of fingers is not lifted within 300 milliseconds after the first finger is lifted.
2. When the number of fingers touching the screen exceeds the set value, the gesture can be recognized.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
