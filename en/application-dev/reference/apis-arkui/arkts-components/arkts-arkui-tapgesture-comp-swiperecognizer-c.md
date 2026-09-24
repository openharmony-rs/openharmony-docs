# SwipeRecognizer

```TypeScript
declare class SwipeRecognizer extends GestureRecognizer
```

Implements a swipe gesture recognizer. Inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md).

**Inheritance/Implementation:** SwipeRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): SwipeDirection
```

Obtains the direction for recognizing swipe gestures.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeDirection](arkts-arkui-tapgesture-comp-swipedirection-e.md) | Direction for recognizing swipe gestures. |

## getVelocityThreshold

```TypeScript
getVelocityThreshold(): number
```

Obtains the minimum velocity required for the swipe gesture to be recognized.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum velocity required for the swipe gesture to be recognized, in vp/s.<br>Value range: [0, +∞) |
