# PinchRecognizer

```TypeScript
declare class PinchRecognizer extends GestureRecognizer
```

Defines the pinch gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying the minimum recognition distance threshold of the pinch gesture. It is applicable to querying the recognition configuration of scaling gestures.

**Inheritance/Implementation:** PinchRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 18

<!--Device-unnamed-declare class PinchRecognizer extends GestureRecognizer--><!--Device-unnamed-declare class PinchRecognizer extends GestureRecognizer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDistance

```TypeScript
getDistance(): number
```

Obtains the minimum distance required for the pinch gesture to be recognized.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PinchRecognizer-getDistance(): number--><!--Device-PinchRecognizer-getDistance(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum distance required for the pinch gesture to be recognized, in vp.<br>Value range: [0, +∞) |
