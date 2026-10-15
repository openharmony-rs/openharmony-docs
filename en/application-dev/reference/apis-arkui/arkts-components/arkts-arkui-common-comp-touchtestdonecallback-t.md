# TouchTestDoneCallback

```TypeScript
declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void
```

Defines the callback event type for dynamically specifying whether a gesture recognizer participates in gesture processing. The lifecycle of the parameters in the callback follows the callback itself, and the methods in the parameters can be used only synchronously within the callback.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-unnamed-declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void--><!--Device-unnamed-declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md) | Yes | Basic gesture event information after [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) completes.<br>**NOTE:** <br>Only **BaseGestureEvent** information is contained, excluding child class extensions.<br>The values of **axisHorizontal** and **axisVertical** are **0**. |
| recognizers | Array&lt;[GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)&gt; | Yes | All gesture recognizers after [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) completes. |
