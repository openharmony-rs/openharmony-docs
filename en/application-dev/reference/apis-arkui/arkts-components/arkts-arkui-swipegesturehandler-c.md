# SwipeGestureHandler

Defines a swipe gesture handler object.

**Inheritance/Implementation:** SwipeGestureHandler extends GestureHandler<SwipeGestureHandler>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: SwipeGestureHandlerOptions)
```

Constructor used to create a swipe gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SwipeGestureHandlerOptions](arkts-arkui-swipegesturehandleroptions-i.md) | No | Parameters of the swipe gesture handler. |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): SwipeGestureHandler
```

Sets the callback for successful swipe gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful swipe gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeGestureHandler](arkts-arkui-swipegesturehandler-c.md) | Swipe gesture handler object. |
