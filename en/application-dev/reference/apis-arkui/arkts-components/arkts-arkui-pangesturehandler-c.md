# PanGestureHandler

Defines a pan gesture handler object.

**Inheritance/Implementation:** PanGestureHandler extends GestureHandler<PanGestureHandler>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: PanGestureHandlerOptions)
```

Constructor used to create a pan gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PanGestureHandlerOptions](arkts-arkui-pangesturehandleroptions-i.md) | No | Parameters of the pan gesture handler. |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): PanGestureHandler
```

Sets the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;void&gt; | Yes | Callback invoked when the pan gesture is cancelled. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for pan gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked when the pan gesture is cancelled. Gesture event information is returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for pan gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked when pan gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionStart

```TypeScript
onActionStart(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for successful pan gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful pan gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) | Pan gesture handler object. |

## onActionUpdate

```TypeScript
onActionUpdate(event: Callback<GestureEvent>): PanGestureHandler
```

Sets the callback for pan gesture movement updates. The callback is triggered when the pan gesture moves.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [Callback](arkts-arkui-callback-i.md)&lt;[GestureEvent](arkts-arkui-gestureevent-i.md)&gt; | Yes | Callback invoked during pan gesture movement.<br>If **fingerList** contains multiple fingers, this callback updates the location information of only one finger each time. |

**Return value:**

| Type | Description |
| --- | --- |
| [PanGestureHandler](arkts-arkui-pangesturehandler-c.md) | Pan gesture handler object. |
