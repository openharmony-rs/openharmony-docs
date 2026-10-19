# Types

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=972ffdace65f823e918481b5e955b2eb18ffaa1a translatedAt=2026-08-05T03:07:27.258Z pushedAt=2026-08-06T01:56:51.149Z -->

This section introduces ArkUI UIContext-related types, including custom component building, UIObserver event listening callbacks, node identifier, cursor style, and context.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## CustomBuilderWithId<sup>18+</sup>

type CustomBuilderWithId = (id: number) =&gt; void

Defines a type that can be used for component attributes and method parameters to customize the UI description and generate custom components with a specific component ID.

**Atomic service API**: This API can be used in atomic services since API version 18.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| id | number | Yes| Component ID.|

## ClickEventListenerCallback<sup>12+</sup>

type ClickEventListenerCallback = (event: ClickEvent, node?: FrameNode) => void

Defines the callback type for listening for click events in **UIObserver**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| event | [ClickEvent](../apis-arkui/arkui-ts/ts-universal-events-click.md#clickevent) | Yes| Information about the click event that triggers the event listener.|
| node | [FrameNode](js-apis-arkui-frameNode.md) | No | Bound component of the click event that triggers the event listener. When this parameter is not passed, the default value is **undefined**. |

## PanListenerCallback<sup>19+</sup>

type PanListenerCallback = (event: GestureEvent, current: GestureRecognizer, node?: FrameNode) => void

Defines the callback type for pan gesture event listening. It can be used in scenarios where you need to listen for pan gesture interactions such as dragging and translating components.

**Atomic service API**: This API can be used in atomic services since API version 19.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type             | Mandatory| Description                               |
| ------- | ----------------- | ---- | --------------------------------- |
| event   | [GestureEvent](../apis-arkui/arkui-ts/ts-gesture-common.md#gestureevent)      | Yes  | Information about the gesture event that triggers the listener.  |
| current | [GestureRecognizer](arkui-ts/ts-gesture-common.md#gesturerecognizer12) | Yes  | Information about the gesture recognizer that triggers the listener. |
| node | [FrameNode](js-apis-arkui-frameNode.md) | No | Component to which the gesture event that triggers the event listener is bound. If this parameter is not passed, the default value is **undefined**. |

## GestureEventListenerCallback<sup>12+</sup>

type GestureEventListenerCallback = (event: GestureEvent, node?: FrameNode) => void

Defines the callback type for gesture event listeners in **UIObserver**.

**Atomic service API**: This API can be used in atomic services since API version 12.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory| Description                         |
| ------- | ------ | ---- | --------------------------- |
| event | [GestureEvent](../apis-arkui/arkui-ts/ts-gesture-common.md#gestureevent) | Yes| Information about the gesture event that triggers the listener.|
| node | [FrameNode](js-apis-arkui-frameNode.md) | No| Component bound to the gesture event that triggers the listener.|

## NodeIdentity<sup>20+</sup>

type NodeIdentity = string \| number

Defines the component ID.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Type             | Description                               |
| ----------------- | --------------------------------- |
| string      | ID of the component, which is set through the universal attribute [id](./arkui-ts/ts-universal-attributes-component-id.md#id).   |
| number | Unique ID assigned by the system to the node, which can be obtained through [getUniqueId](js-apis-arkui-frameNode.md#getuniqueid12).  |

## NodeRenderStateChangeCallback<sup>20+</sup>

type NodeRenderStateChangeCallback = (state: NodeRenderState, node?: FrameNode) => void

Defines the callback type for listening for the rendering state of a specific node in **UIObserver**.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type             | Mandatory| Description                               |
| ------- | ----------------- | ---- | --------------------------------- |
| state | [NodeRenderState](arkts-apis-uicontext-e.md#noderenderstate20) | Yes | Current render state of the node, which indicates whether the monitored node is in a renderable state. |
| node | [FrameNode](js-apis-arkui-frameNode.md) | No | Component that triggers the render state change listener. When you need to obtain the node information of the component whose render state has changed, you can obtain it through this parameter. If the component is released, null is returned. If this parameter is not passed, the default value is **undefined**. |

## GestureListenerCallback<sup>20+</sup>

type GestureListenerCallback = (info: GestureTriggerInfo) => void

Defines the callback type for listening for specific gesture trigger information in **UIObserver**.

**Atomic service API**: This API can be used in atomic services since API version 20.

**Model restriction:** This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type             | Mandatory| Description                               |
| ------- | ----------------- | ---- | --------------------------------- |
| info   | [GestureTriggerInfo](arkts-apis-uicontext-i.md#gesturetriggerinfo20)     | Yes  |  Details of the gesture triggered by the interaction.|

## PointerStyle<sup>12+</sup>

type PointerStyle = pointer.PointerStyle

Defines the pointer style.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.MultimodalInput.Input.Pointer

|Type|Description|
| -- | -- |
|[pointer.PointerStyle](../apis-input-kit/js-apis-pointer.md#pointerstyle) |Pointer style.|

## Context<sup>12+</sup>

type Context = common.Context

Context of the Ability (app component) where the current component resides.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Model restriction**: This API can be used only in the stage model.

| Type|Description  |
| ------ | ------------------- |
| [common.Context](../apis-ability-kit/js-apis-app-ability-common.md#context) |Context object associated with the current ability.|

## OnOverlayBackPressCallback

type OnOverlayBackPressCallback = () => boolean

Defines the callback type for intercepting the overlay swipe-back event.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type | Description |
| -------- | -------- |
| boolean | Whether to intercept the back event.<br/>The value **true** indicates that the back event is intercepted and will not be passed to lower-level components; the value **false** indicates that the event is not intercepted and will be passed through to lower-level components. |