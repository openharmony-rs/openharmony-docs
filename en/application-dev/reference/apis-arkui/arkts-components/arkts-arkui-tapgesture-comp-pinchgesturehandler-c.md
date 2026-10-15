# PinchGestureHandler

```TypeScript
declare class PinchGestureHandler extends GestureHandler<PinchGestureHandler>
```

Defines the pinch gesture handler object type, which is used to recognize multi-finger pinch interactions on a component. It is suitable for scaling operation scenarios, and supports configuring recognition conditions such as the number of triggering fingers, the minimum recognition distance, and the finger count limit.

**Inheritance/Implementation:** PinchGestureHandler extends GestureHandler&lt;PinchGestureHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class PinchGestureHandler extends GestureHandler<PinchGestureHandler>--><!--Device-unnamed-declare class PinchGestureHandler extends GestureHandler<PinchGestureHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: PinchGestureHandlerOptions)
```

Constructor used to create a pinch gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandler-constructor(options?: PinchGestureHandlerOptions)--><!--Device-PinchGestureHandler-constructor(options?: PinchGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PinchGestureHandlerOptions](arkts-arkui-tapgesture-comp-pinchgesturehandleroptions-i.md) | No | Configuration parameters of the pinch gesture handler. Pass this parameter when you need to customize the minimum finger count for triggering a pinch, the minimum recognition distance, or the finger count check. If this parameter is not passed, the default configuration of the pinch gesture handler is used, for example, the trigger finger count is 2, the minimum recognition distance is 5 vp, and the finger count on the touch screen is not checked by default. |

<a id="onactioncancel1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): PinchGestureHandler
```

Sets the callback for pinch gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandler-onActionCancel(event: Callback<void>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionCancel(event: Callback<void>): PinchGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when the pinch gesture is cancelled. No gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) | Pinch gesture handler object. |

<a id="onactioncancel2"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for pinch gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel1), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PinchGestureHandler-onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when the pinch gesture is cancelled. Gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for pinch gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandler-onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when pinch gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for successful pinch gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandler-onActionStart(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionStart(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful pinch gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for pinch gesture movement updates. The callback is triggered when the pinch gesture moves.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PinchGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler--><!--Device-PinchGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked during pinch gesture movement. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-tapgesture-comp-pinchgesturehandler-c.md) | Pinch gesture handler object. |
