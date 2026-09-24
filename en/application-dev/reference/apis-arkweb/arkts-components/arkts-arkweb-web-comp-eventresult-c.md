# EventResult

```TypeScript
declare class EventResult
```

EventResult is a class in ArkWeb Kit used to notify the **Web** component of the same-layer event consumption result. In same-layer embedding scenarios, the app and the **Web** component are both exposed in the event response chain. EventResult allows the app to declare to the **Web** component whether it has consumed a touch or mouse event, thereby determining whether the **Web** component continues to process the event. When the app sets the consumption result to **true**, it indicates that the app has consumed the event and the **Web** component will no longer consume it. When set to **false**, it indicates that the app does not consume the event, and the event will be consumed by the **Web** component. EventResult is used to set the consumption result of touch events ([TouchType](../../apis-arkui/arkts-apis/arkts-arkui-touchtype-e.md)) and mouse events ([MouseAction](../../apis-arkui/arkts-apis/arkts-arkui-mouseaction-e.md), limited to left, middle, and right buttons), with the mouse button type defined by MouseButton. It is applicable to event coordination scenarios where the app and the **Web** component interact at the same layer.

For details about the sample code of the touch event, see [onNativeEmbedGestureEvent](arkts-arkweb-web-comp-attribute.md#onnativeembedgestureevent).

For details about the sample code of the mouse event, see [onNativeEmbedMouseEvent](arkts-arkweb-web-comp-attribute.md#onnativeembedmouseevent).

**Since:** 12

**System capability:** SystemCapability.Web.Webview.Core

## constructor

```TypeScript
constructor()
```

Constructs a **EventResult** object.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

## setGestureEventResult

```TypeScript
setGestureEventResult(result: boolean): void
```

Sets the gesture event consumption result.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | boolean | Yes | Whether to consume the gesture event.<br>The value **true** means to consume the gesture event, and **false** means the opposite. <br>If **null** or **undefined** is passed in, the value is **true**. |

**Examples**

For details, see [onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent).

<a id="setgestureeventresult-1"></a>

## setGestureEventResult

```TypeScript
setGestureEventResult(result: boolean, stopPropagation: boolean): void
```

Sets the gesture event consumption result and bubbling control.

**Since:** 14

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | boolean | Yes | Whether to consume the gesture event.<br>The value **true** means to consume the gesture event, and **false** means the opposite. <br>If **null** or **undefined** is passed in, the value is **true**. |
| stopPropagation | boolean | Yes | Whether to stop propagation. This parameter is valid only when **result** is set to **true**.<br>The value **true** means to stop propagation, and **false** means the opposite. <br>If **null** or **undefined** is passed in, the value is **true**. |

**Examples**

For details, see [onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent).

## setMouseEventResult

```TypeScript
setMouseEventResult(result: boolean, stopPropagation?: boolean): void
```

Sets the mouse event consumption result and bubbling control.

**Since:** 20

**System capability:** SystemCapability.Web.Webview.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| result | boolean | Yes | Whether to consume the mouse event.<br>true indicates consumption of the mouse event, and false indicates no consumption of the mouse event. <br>The value is true when null or undefined is passed in. |
| stopPropagation | boolean | No | Whether to stop bubbling. This parameter takes effect only when result is true.<br>true indicates that bubbling is stopped, and false indicates that bubbling is not stopped. <br>The value is true when null or undefined is passed in. <br>Default value: true. |

**Examples**

For details about the sample code of the mouse event, see [onNativeEmbedMouseEvent](./arkts-basic-components-web-events.md#onnativeembedmouseevent).
