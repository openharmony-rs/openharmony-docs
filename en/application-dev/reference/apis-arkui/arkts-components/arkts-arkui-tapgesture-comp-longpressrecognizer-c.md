# LongPressRecognizer

```TypeScript
declare class LongPressRecognizer extends GestureRecognizer
```

Implements a long press gesture recognizer. Inherits from [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md).

**Inheritance/Implementation:** LongPressRecognizer extends [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getAllowableMovement

```TypeScript
getAllowableMovement(): number
```

Obtains the maximum movement distance allowed for gesture recognition by the long press gesture recognizer.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Maximum movement distance recognized by the long press gesture recognizer, in px.<br>Value range: (0, +∞) |

## getDuration

```TypeScript
getDuration(): number
```

Obtains the minimum duration required for the long press gesture to be recognized.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| number | Minimum duration, in ms.<br>Value range: [0, +∞) |

## isRepeat

```TypeScript
isRepeat(): boolean
```

Checks whether the long press gesture recognizer is set to trigger repeated callbacks.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the long press gesture recognizer is set to trigger repeated callbacks. **false**: Repeated callbacks are not triggered. **true**: Repeated callbacks are triggered. |
