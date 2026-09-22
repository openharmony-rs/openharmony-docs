# TouchTestDoneCallback

```TypeScript
declare type TouchTestDoneCallback = (event: BaseGestureEvent, recognizers: Array<GestureRecognizer>) => void
```

Represents the callback type for dynamically specifying gesture recognizer participation in gesture processing.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [BaseGestureEvent](arkts-arkui-tapgesture-comp-basegestureevent-i.md) | Yes | Basic gesture event information after [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) completes.<br>**NOTE:** <br>Only **BaseGestureEvent** information is contained, excluding child class extensions.<br>The values of **axisHorizontal** and **axisVertical** are **0**. |
| recognizers | Array&lt;[GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)&gt; | Yes | All gesture recognizers after [hit testing](../../../ui/arkts-interaction-basic-principles.md#hit-testing) completes. |
