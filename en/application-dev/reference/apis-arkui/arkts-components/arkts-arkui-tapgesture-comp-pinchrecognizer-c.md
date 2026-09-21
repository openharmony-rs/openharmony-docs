# PinchRecognizer

```TypeScript
declare class PinchRecognizer extends GestureRecognizer
```

Implements a pinch gesture recognizer. Inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md).

**Inheritance/Implementation:** PinchRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDistance

```TypeScript
getDistance(): number
```

Obtains the minimum distance required for the pinch gesture to be recognized.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum distance required for the pinch gesture to be recognized, in vp.<br>Value range: [0, +∞) |
