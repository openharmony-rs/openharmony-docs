# GestureRecognizerJudgeBeginCallback

```TypeScript
declare type GestureRecognizerJudgeBeginCallback = (event: BaseGestureEvent, current: GestureRecognizer, recognizers: Array<GestureRecognizer>,
  touchRecognizers?: Array<TouchRecognizer>) => GestureJudgeResult
```

Represents a custom gesture recognizer judgment callback type.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [BaseGestureEvent](arkts-arkui-basegestureevent-i.md) | Yes | Information about the current basic gesture event. |
| current | [GestureRecognizer](arkts-arkui-gesturerecognizer-c.md) | Yes | Gesture recognizer object that is about to respond. |
| recognizers | Array&lt;[GestureRecognizer](arkts-arkui-gesturerecognizer-c.md)&gt; | Yes | Other gesture recognizer objects in the response chain. |
| touchRecognizers | Array&lt;[TouchRecognizer](arkts-arkui-touchrecognizer-c.md)&gt; | No | Touch recognizers in the response chain. The default value is **null**, indicating no responsive touch recognizers in the current gesture-bound component and its descendants. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureJudgeResult](arkts-arkui-gesturejudgeresult-e.md) | Judgment result indicating whether gesture recognition succeeds. |
