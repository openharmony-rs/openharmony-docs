# GestureCollectInterceptCallback

```TypeScript
declare type GestureCollectInterceptCallback = (recognizers: Array<GestureRecognizer>,
   touchRecognizers?: Array<TouchRecognizer>) => GestureCollectIntervention
```

Defines the callback type used in [onGestureCollectIntercept](arkts-arkui-common-comp-commonmethod-c.md#ongesturecollectintercept).

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| recognizers | Array&lt;[GestureRecognizer](arkts-arkui-tapgesture-comp-gesturerecognizer-c.md)&gt; | Yes | Gesture recognizer objects of the component on the response chain. |
| touchRecognizers | Array&lt;[TouchRecognizer](arkts-arkui-tapgesture-comp-touchrecognizer-c.md)&gt; | No | Touch recognizer objects of the component on the response chain.<br>The default value is **null**. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureCollectIntervention](../arkts-apis/arkts-arkui-gesturecollectintervention-e.md) | Gesture collection intervention result. |
