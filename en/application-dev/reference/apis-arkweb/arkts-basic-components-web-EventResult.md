# Class (EventResult)

<!--Kit: ArkWeb-->
<!--Subsystem: Web-->
<!--Owner: @zhanghaozhi1-->
<!--Designer: @dzichou-->
<!--Tester: @ghiker-->
<!--Adviser: @HelloShuo-->
<!-- md-trans-meta sourceCommit=4f3e4630cb3a92ec0ab1a250c999a60e5b0e99de translatedAt=2026-08-07T04:36:49.332Z pushedAt=2026-08-07T08:12:04.345Z -->

EventResult is a class in ArkWeb Kit used to notify the **Web** component of the same-layer event consumption result. In same-layer embedding scenarios, the app and the **Web** component are both exposed in the event response chain. EventResult allows the app to declare to the **Web** component whether it has consumed a touch or mouse event, thereby determining whether the **Web** component continues to process the event. When the app sets the consumption result to **true**, it indicates that the app has consumed the event and the **Web** component will no longer consume it. When set to **false**, it indicates that the app does not consume the event, and the event will be consumed by the **Web** component. EventResult is used to set the consumption result of touch events ([TouchType](../apis-arkui/arkui-ts/ts-appendix-enums.md#touchtype)) and mouse events ([MouseAction](../apis-arkui/arkui-ts/ts-appendix-enums.md#mouseaction8), limited to left, middle, and right buttons), with the mouse button type defined by [MouseButton](../apis-arkui/arkui-ts/ts-appendix-enums.md#mousebutton8). It is applicable to event coordination scenarios where the app and the **Web** component interact at the same layer.

For details about the sample code of the touch event, see [onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent11).

For details about the sample code of the mouse event, see [onNativeEmbedMouseEvent](./arkts-basic-components-web-events.md#onnativeembedmouseevent20).

> **NOTE**
>
> - The initial APIs of this component are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this class are supported since API version 12.
>
> - The sample effect is subject to the actual device.

## constructor<sup>12+</sup>

constructor()

Constructs a **EventResult** object.

**System capability**: SystemCapability.Web.Webview.Core

## setGestureEventResult<sup>12+</sup>

setGestureEventResult(result: boolean): void

Sets the gesture event consumption result.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type| Mandatory | Description            |
| --------------- | -------- | ----  |------- |
| result          | boolean  | Yes   | Whether to consume the gesture event.<br>The value **true** means to consume the gesture event, and **false** means the opposite.<br>If **null** or **undefined** is passed in, the value is **true**.|

**Example**

For details, see [onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent11).

## setGestureEventResult<sup>14+</sup>

setGestureEventResult(result: boolean, stopPropagation: boolean): void

Sets the gesture event consumption result and bubbling control.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type| Mandatory | Description            |
| --------------- | -------- | ----  |------- |
| result          | boolean  | Yes   | Whether to consume the gesture event.<br>The value **true** means to consume the gesture event, and **false** means the opposite.<br>If **null** or **undefined** is passed in, the value is **true**.|
| stopPropagation | boolean  | Yes  | Whether to stop propagation. This parameter is valid only when **result** is set to **true**.<br>The value **true** means to stop propagation, and **false** means the opposite.<br>If **null** or **undefined** is passed in, the value is **true**.|

**Example**

For details, see [onNativeEmbedGestureEvent](./arkts-basic-components-web-events.md#onnativeembedgestureevent11).

## setMouseEventResult<sup>20+</sup>

setMouseEventResult(result: boolean, stopPropagation?: boolean): void

Sets the mouse event consumption result and bubbling control.

**System capability**: SystemCapability.Web.Webview.Core

**Parameters**

| Name         | Type| Mandatory | Description            |
| --------------- | -------- | ----  |------- |
| result          | boolean  | Yes    | Whether to consume the mouse event.<br>true indicates consumption of the mouse event, and false indicates no consumption of the mouse event.<br>The value is true when null or undefined is passed in.|
| stopPropagation | boolean  | No   | Whether to stop bubbling. This parameter takes effect only when result is true.<br>true indicates that bubbling is stopped, and false indicates that bubbling is not stopped.<br>The value is true when null or undefined is passed in.<br>Default value: true. |

**Example**

For details about the sample code of the mouse event, see [onNativeEmbedMouseEvent](./arkts-basic-components-web-events.md#onnativeembedmouseevent20).
<!--no_check-->