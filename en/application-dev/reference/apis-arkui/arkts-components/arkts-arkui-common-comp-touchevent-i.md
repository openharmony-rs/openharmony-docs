# TouchEvent

```TypeScript
declare interface TouchEvent extends BaseEvent
```

Inherits from [BaseEvent](arkts-arkui-common-comp-baseevent-i.md). In non-event injection scenarios, **changedTouches** contains points resampled at the screen refresh rate, while **touches** contains points reported at the device's refresh rate. As such, **changedTouches** data may differ from **touches**.

**Inheritance/Implementation:** TouchEvent extends [BaseEvent](arkts-arkui-common-comp-baseevent-i.md)

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## getHistoricalPoints

```TypeScript
getHistoricalPoints(): Array<HistoricalPoint>
```

Obtains all historical touch points for the current frame. The touch event frequency per frame varies by device. This API can be called only in [TouchEvent](arkts-arkui-common-comp-touchevent-i.md). This API is only available within [TouchEvent](arkts-arkui-common-comp-touchevent-i.md) during [onTouch](arkts-arkui-common-comp-commonmethod-c.md#ontouch) invocations. Typically, [onTouch](arkts-arkui-common-comp-commonmethod-c.md#ontouch) is invoked once per frame. If multiple [TouchEvent](arkts-arkui-common-comp-touchevent-i.md) instances are received in a single frame, the last point is returned through **onTouch**, and the remaining points are stored as historical points. For multi-touch events within the same frame, multiple** onTouch** calls may occur.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[HistoricalPoint](arkts-arkui-common-comp-historicalpoint-i.md)&gt; | Array of historical points. |

## preventDefault

```TypeScript
preventDefault: () => void
```

Blocks the default event.

**NOTE:** 

This API is only supported by the Hyperlink component. Using it with unsupported components throws an exception. Asynchronous calls and **Modifier** API integration are not yet supported.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100017](../errorcode-event.md#100017-component-does-not-support-default-event-prevention) | Component does not support prevent function. |

## stopPropagation

```TypeScript
stopPropagation: () => void
```

Disables [event bubbling](../../../ui/arkts-interaction-basic-principles.md#event-bubbling) propagation.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## changedTouches

```TypeScript
changedTouches: TouchObject[]
```

Information about touch points that changed and triggered the event. When using this property, you need to check whether it is empty.

**Type:** [TouchObject](arkts-arkui-common-comp-touchobject-i.md)[]

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## eventHandleId

```TypeScript
eventHandleId?: number
```

Unique identifier for event processing.

Value range: [0, +∞)

**NOTE:** 

This field is used when dispatching events using the [postInputEventWithStrategy](../arkts-apis/arkts-arkui-buildernode-c.md#postinputeventwithstrategy) API. Each time an event is dispatched, this field is increased by 100000.

Using the same **eventHandleId** for multiple event dispatches will cause abnormal event responses. This field only needs to be assigned when constructing an event; developers do not need to handle it in other cases.

**Type:** number

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## touches

```TypeScript
touches: TouchObject[]
```

Information about all touch points (for multi-touch). Each element represents one touch point. When using this property, you need to check whether it is empty.

**Type:** [TouchObject](arkts-arkui-common-comp-touchobject-i.md)[]

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## type

```TypeScript
type: TouchType
```

Type of the touch event.

**Type:** [TouchType](../arkts-apis/arkts-arkui-touchtype-e.md)

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
