# TapRecognizer

```TypeScript
declare class TapRecognizer extends GestureRecognizer
```

Implements a tap gesture recognizer object. Inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md).

**Inheritance/Implementation:** TapRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getTapCount

```TypeScript
getTapCount(): number
```

Obtains the number of consecutive taps required for the tap gesture to be recognized.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Number of consecutive taps required for the tap gesture to be recognized.<br>Value range: [0, +∞) |
