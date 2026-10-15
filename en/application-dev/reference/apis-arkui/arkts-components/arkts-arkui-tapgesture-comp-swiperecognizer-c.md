# SwipeRecognizer

```TypeScript
declare class SwipeRecognizer extends GestureRecognizer
```

Defines the swipe gesture recognizer object, which inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) and supports querying the velocity threshold and swipe direction of the swipe gesture. It is applicable to querying the swipe gesture recognition configuration.

**Inheritance/Implementation:** SwipeRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 18

<!--Device-unnamed-declare class SwipeRecognizer extends GestureRecognizer--><!--Device-unnamed-declare class SwipeRecognizer extends GestureRecognizer-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getDirection

```TypeScript
getDirection(): SwipeDirection
```

Obtains the direction for recognizing swipe gestures.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SwipeRecognizer-getDirection(): SwipeDirection--><!--Device-SwipeRecognizer-getDirection(): SwipeDirection-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeDirection](arkts-arkui-tapgesture-comp-swipedirection-e.md) | Direction for recognizing swipe gestures. |

## getVelocityThreshold

```TypeScript
getVelocityThreshold(): number
```

Returns the minimum velocity threshold for the preset swipe gesture recognizer to recognize a swipe. The default minimum velocity is 100 vp/s.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-SwipeRecognizer-getVelocityThreshold(): number--><!--Device-SwipeRecognizer-getVelocityThreshold(): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum velocity threshold for the preset swipe gesture recognizer to recognize a swipe, in vp/s. If no velocity threshold is configured, the default value 100vp/s is returned.<br>Value range: [0, +∞) |
