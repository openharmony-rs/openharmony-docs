# GestureGroupHandler

```TypeScript
declare class GestureGroupHandler extends GestureHandler<GestureGroupHandler>
```

Defines the gesture group handler object type, which is used to combine multiple gestures and bind them to a component as a whole. It is suitable for scenarios where the recognition order or concurrency relationship of multiple gestures such as single tap, double tap, and long press needs to be coordinated.

**Inheritance/Implementation:** GestureGroupHandler extends GestureHandler&lt;GestureGroupHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class GestureGroupHandler extends GestureHandler<GestureGroupHandler>--><!--Device-unnamed-declare class GestureGroupHandler extends GestureHandler<GestureGroupHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: GestureGroupGestureHandlerOptions)
```

Constructor used to create a gesture group handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureGroupHandler-constructor(options?: GestureGroupGestureHandlerOptions)--><!--Device-GestureGroupHandler-constructor(options?: GestureGroupGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [GestureGroupGestureHandlerOptions](arkts-arkui-tapgesture-comp-gesturegroupgesturehandleroptions-i.md) | No | Configuration options of the gesture group handler. Passed when the combined gesture recognition mode and gesture set need to be set; if not passed, the default configuration of the gesture group handler is used, with the combined gesture recognition mode defaulting to **GestureMode.Sequence** and no gesture set configured. |

## onCancel

```TypeScript
onCancel(event: Callback<void>): GestureGroupHandler
```

Sets the cancellation callback for the gesture group handler. The callback is triggered when a sequence gesture ([GestureMode](arkts-arkui-tapgesture-comp-gesturemode-e.md).Sequence) is cancelled.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GestureGroupHandler-onCancel(event: Callback<void>): GestureGroupHandler--><!--Device-GestureGroupHandler-onCancel(event: Callback<void>): GestureGroupHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback for the gesture group handler cancellation, which takes no input parameter and is used to receive a notification after the sequential combined gesture is canceled. |

**Return value:**

| Type | Description |
| --- | --- |
| [GestureGroupHandler](arkts-arkui-tapgesture-comp-gesturegrouphandler-c.md) | Current gesture group handler object. |
