# LongPressGestureHandler

```TypeScript
declare class LongPressGestureHandler extends GestureHandler<LongPressGestureHandler>
```

Defines the long press gesture handler object type, which is used to recognize long press interactions on a component. It is suitable for scenarios where an operation is triggered after pressing and holding, and supports configuring recognition conditions such as the number of triggering fingers, the long press duration, whether to trigger continuously, and the movement threshold.

**Inheritance/Implementation:** LongPressGestureHandler extends GestureHandler&lt;LongPressGestureHandler&gt;

**Since:** 12

<!--Device-unnamed-declare class LongPressGestureHandler extends GestureHandler<LongPressGestureHandler>--><!--Device-unnamed-declare class LongPressGestureHandler extends GestureHandler<LongPressGestureHandler>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor(options?: LongPressGestureHandlerOptions)
```

Constructor used to create a long press gesture handler instance.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LongPressGestureHandler-constructor(options?: LongPressGestureHandlerOptions)--><!--Device-LongPressGestureHandler-constructor(options?: LongPressGestureHandlerOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [LongPressGestureHandlerOptions](arkts-arkui-tapgesture-comp-longpressgesturehandleroptions-i.md) | No | Configuration parameters of the long press gesture handler. Pass this parameter when you need to customize the minimum finger count for triggering a long press, whether to trigger continuously, the minimum trigger time, finger count verification, or the maximum movement distance. If this parameter is not passed, the default configuration of the long press gesture handler is used, for example, the trigger finger count is 1, **repeat** is **false**, the minimum time for triggering a long press is 500 ms, and the maximum movement distance is 15 px. |

## onAction

```TypeScript
onAction(event: Callback<GestureEvent>): LongPressGestureHandler
```

Sets the callback for successful long press gesture recognition.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LongPressGestureHandler-onAction(event: Callback<GestureEvent>): LongPressGestureHandler--><!--Device-LongPressGestureHandler-onAction(event: Callback<GestureEvent>): LongPressGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked upon successful long press gesture recognition. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |

<a id="onactioncancel1"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<void>): LongPressGestureHandler
```

Sets the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. No gesture event information is returned.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-LongPressGestureHandler-onActionCancel(event: Callback<void>): LongPressGestureHandler--><!--Device-LongPressGestureHandler-onActionCancel(event: Callback<void>): LongPressGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;void&gt; | Yes | Callback invoked when the long press gesture is cancelled. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |

<a id="onactioncancel2"></a>

## onActionCancel

```TypeScript
onActionCancel(event: Callback<GestureEvent>): LongPressGestureHandler
```

Sets the callback for long press gesture cancellation. This callback is triggered when a touch cancellation event occurs after successful recognition. Compared with [onActionCancel](#onactioncancel1), this API returns gesture event information.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-LongPressGestureHandler-onActionCancel(event: Callback<GestureEvent>): LongPressGestureHandler--><!--Device-LongPressGestureHandler-onActionCancel(event: Callback<GestureEvent>): LongPressGestureHandler-End-->

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

<!--Device-LongPressGestureHandler-onActionEnd(event: Callback<GestureEvent>): LongPressGestureHandler--><!--Device-LongPressGestureHandler-onActionEnd(event: Callback<GestureEvent>): LongPressGestureHandler-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[GestureEvent](arkts-arkui-tapgesture-comp-gestureevent-i.md)&gt; | Yes | Callback invoked when long press gesture recognition completes. |

**Return value:**

| Type | Description |
| --- | --- |
| [LongPressGestureHandler](arkts-arkui-tapgesture-comp-longpressgesturehandler-c.md) | Long press gesture handler object. |
