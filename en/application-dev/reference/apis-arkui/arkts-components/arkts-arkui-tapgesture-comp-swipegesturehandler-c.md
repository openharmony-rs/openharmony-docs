# SwipeGestureHandler

```TypeScript
declare class SwipeGestureHandler extends GestureHandler<SwipeGestureHandler>
```

Defines the swipe gesture handler object type, which is used to recognize quick swipe interactions on a component. It is suitable for scenarios where an operation is triggered based on the swipe direction or speed, and supports configuring the number of triggering fingers, the swipe direction, and the minimum speed.

**Inheritance/Implementation:** SwipeGestureHandler extends GestureHandler&lt;SwipeGestureHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class SwipeGestureHandler extends GestureHandler<SwipeGestureHandler>--><!--Device-unnamed-declare class SwipeGestureHandler extends GestureHandler<SwipeGestureHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: SwipeGestureHandlerOptions)
```

Constructor used to create a swipe gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeGestureHandler-constructor(options?: SwipeGestureHandlerOptions)--><!--Device-SwipeGestureHandler-constructor(options?: SwipeGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [SwipeGestureHandlerOptions](arkts-arkui-tapgesture-comp-swipegesturehandleroptions-i.md) | No | Configuration options of the swipe gesture handler. Pass this parameter when you need to customize the minimum finger count, swipe direction, minimum recognition speed, or finger count check for triggering a swipe; if not passed, the default configuration of the swipe gesture handler is used, that is, the trigger finger count is 1, the direction is **SwipeDirection.All**, the minimum speed is 100 vp/s, and the number of fingers touching the screen is not checked by default. |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): SwipeGestureHandler
```

Sets the callback for successful swipe gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwipeGestureHandler-onAction(event: Callback<GestureEvent>): SwipeGestureHandler--><!--Device-SwipeGestureHandler-onAction(event: Callback<GestureEvent>): SwipeGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful swipe gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [SwipeGestureHandler](arkts-arkui-tapgesture-comp-swipegesturehandler-c.md) | Swipe gesture handler object. |
