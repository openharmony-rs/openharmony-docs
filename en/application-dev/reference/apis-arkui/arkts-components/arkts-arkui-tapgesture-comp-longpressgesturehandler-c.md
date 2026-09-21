# LongPressGestureHandler

```TypeScript
declare class LongPressGestureHandler extends GestureHandler<LongPressGestureHandler>
```

Defines a long press gesture handler object.

**Inheritance/Implementation:** LongPressGestureHandler extends GestureHandler<LongPressGestureHandler>

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: LongPressGestureHandlerOptions)
```

Constructor used to create a long press gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LongPressGestureHandlerOptions](arkts-arkui-tapgesture-comp-longpressgesturehandleroptions-i.md) | No | Parameters of the long press gesture handler. |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): LongPressGestureHandler
```

Sets the callback for successful long press gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful long press gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): LongPressGestureHandler
```

Sets the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when the long press gesture is cancelled. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |

<a id="onactioncancel-1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): LongPressGestureHandler
```

Sets the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when the long press gesture is cancelled. This callback returns gesture event information. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |

## onActionEnd

```TypeScript
onActionEnd(event: Callback<GestureEvent>): LongPressGestureHandler
```

Sets the callback for long press gesture recognition completion. This callback is triggered when all fingers are lifted after successful recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when long press gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |
