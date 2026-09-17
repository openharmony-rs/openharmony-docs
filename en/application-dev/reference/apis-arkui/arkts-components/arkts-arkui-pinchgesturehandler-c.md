# PinchGestureHandler

Defines a type of gesture handler object for pinch gestures.

**Inheritance/Implementation:** PinchGestureHandler extends GestureHandler<PinchGestureHandler>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: PinchGestureHandlerOptions)
```

Constructor used to create a pinch gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PinchGestureHandlerOptions](arkts-arkui-pinchgesturehandleroptions-i.md) | No | Parameters of the pinch gesture handler. |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): PinchGestureHandler
```

Sets the callback for pinch gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the pinch gesture is cancelled. No gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for pinch gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked when the pinch gesture is cancelled. Gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for pinch gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked when pinch gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for successful pinch gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful pinch gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | Pinch gesture handler object. |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): PinchGestureHandler
```

Sets the callback for pinch gesture movement updates. The callback is triggered when the pinch gesture moves.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked during pinch gesture movement. |

**Return value:**

| Type | Description |
| --- | --- |
| [PinchGestureHandler](arkts-arkui-pinchgesturehandler-c.md) | Pinch gesture handler object. |
