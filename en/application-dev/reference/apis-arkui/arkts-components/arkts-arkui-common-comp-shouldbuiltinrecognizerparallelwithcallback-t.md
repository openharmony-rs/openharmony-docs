# ShouldBuiltInRecognizerParallelWithCallback

```TypeScript
declare type ShouldBuiltInRecognizerParallelWithCallback = (current: GestureRecognizer, others: Array<GestureRecognizer>) => GestureRecognizer
```

Represents the callback used to set the parallel relationship between built-in gestures and gestures of other components in the response chain.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| current | [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) | Yes | Built-in gesture recognizer of the current component. Currently only a built- in gesture recognizer of the [GestureType](arkts-arkui-tapgesture-comp-gesturetype-e.md).PAN_GESTURE type is supported. |
| others | Array&lt;[GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)&gt; | Yes | Gesture recognizers of the same type from other components with higher priority in the response chain. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md) | Gesture recognizer that is bound in parallel with the current recognizer. |
