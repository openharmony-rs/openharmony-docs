# PanGestureHandler

```TypeScript
declare class PanGestureHandler extends GestureHandler<PanGestureHandler>
```

Defines the pan gesture handler object type, which is used to recognize drag or slide interactions on a component. It is suitable for scenarios where the state needs to be updated as the finger moves, and supports configuring the number of triggering fingers, the pan direction, the minimum drag distance, and the trigger distance for different input sources.

**Inheritance/Implementation:** PanGestureHandler extends GestureHandler&lt;PanGestureHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class PanGestureHandler extends GestureHandler<PanGestureHandler>--><!--Device-unnamed-declare class PanGestureHandler extends GestureHandler<PanGestureHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: PanGestureHandlerOptions)
```

Constructor used to create a pan gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PanGestureHandler-constructor(options?: PanGestureHandlerOptions)--><!--Device-PanGestureHandler-constructor(options?: PanGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-tapgesture-comp-pangesturehandleroptions-i.md) | No | Configuration options of the pan gesture handler. Pass this parameter when you need to customize the minimum number of fingers to trigger dragging, the trigger direction, the minimum drag distance, the minimum drag distance for different input sources, or finger count validation. If this parameter is not passed, the default configuration of the pan gesture handler is used, for example, the number of fingers to trigger is 1, the direction is **PanDirection.All**, the minimum drag distance uses the default value based on the input source, and the number of fingers touching the screen is not checked by default. |

<a id="onactioncancel1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): PanGestureHandler
```

Sets the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PanGestureHandler-onActionCancel(event: Callback<void>): PanGestureHandler--><!--Device-PanGestureHandler-onActionCancel(event: Callback<void>): PanGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when the pan gesture is cancelled. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) | Pan gesture handler object. |

<a id="onactioncancel2"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel1), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-PanGestureHandler-onActionCancel(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionCancel(event: Callback<GestureEvent>): PanGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when the pan gesture is cancelled. Gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for pan gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PanGestureHandler-onActionEnd(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionEnd(event: Callback<GestureEvent>): PanGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when pan gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for successful pan gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PanGestureHandler-onActionStart(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionStart(event: Callback<GestureEvent>): PanGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful pan gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for pan gesture movement updates. The callback is triggered when the pan gesture moves.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-PanGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler--><!--Device-PanGestureHandler-onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked during pan gesture movement.<br>If **fingerList** contains multiple fingers, this callback updates the location information of only one finger each time. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-tapgesture-comp-pangesturehandler-c.md) | Pan gesture handler object. |
