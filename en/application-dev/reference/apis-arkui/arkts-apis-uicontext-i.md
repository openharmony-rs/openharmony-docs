# Interfaces (Others)

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yihao-lin; @liyi0903; @mayaolll-->
<!--Designer: @piggyguy; @liyi0903; @fangzhiyuan1-->
<!--Tester: @fredyuan912-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=4cffd417ce4153840a6f1321b4778e89f34ef96c translatedAt=2026-08-05T03:09:16.081Z pushedAt=2026-08-06T01:03:36.547Z -->

This section summarizes other ArkUI UIContext-related interfaces, which are used to describe component target nodes, page information, OverlayManager initialization parameters, gesture trigger information, Swiper content area information, and more.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs of this module can only be used in the stage model.

## TargetInfo<sup>18+</sup>

Specifies the target node for component binding.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| id | string&nbsp;\|&nbsp;number | No | No | Specifies the target node bound to the popup or menu.<br>**Note:** <br>1. When **id** is of the number type, it corresponds to **UniqueID** of the component instance, and the uniqueness of this ID is guaranteed by the system.<br/>2. When **id** is of the string type, it corresponds to the component specified by the [universal attribute id](arkui-ts/ts-universal-attributes-component-id.md#id), and the uniqueness of this ID must be ensured by the you. However, there may be multiple components with the same ID in practice. |
| componentId | number | No | Yes | **UniqueID** of the custom component where the target node is located. When the above **id** is specified as the string type and the target node needs to be found within a specified custom component scope, this property can be used to define the scope, making it easier for you to ensure the uniqueness of **id: string** within a certain range. By default, no custom component scope is specified. |

## PageInfo<sup>12+</sup>

Represents the page information of the router or navigation destination. If there is no related page information, **undefined** is returned.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- |-------- | -------- |
| routerPageInfo | observer.[RouterPageInfo](js-apis-arkui-observer.md#routerpageinfo) | No|Yes| Router information.|
| navDestinationInfo | observer.[NavDestinationInfo](js-apis-arkui-observer.md#navdestinationinfo) | No|Yes| Navigation destination information.|

## OverlayManagerOptions<sup>15+</sup>

Provides the parameters used for initializing [OverlayManager](arkts-apis-uicontext-overlaymanager.md).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name            | Type               | Read-Only| Optional  | Description                    |
| --------------- | ---------------------- | ------------ | --------------------- | --------------------- |
| renderRootOverlay   | boolean | No  | Yes | Whether to render the overlay root node. The value **true** indicates that the overlay root node is rendered, and **false** indicates the opposite. The default value is **true**. By setting this parameter to **false**, you can resolve the issue where [PhotoPickerComponent](../apis-media-library-kit/ohos-file-PhotoPickerComponent.md) cannot select photos when [OverlayManager](arkts-apis-uicontext-overlaymanager.md) is displayed on top of it.<br>**Atomic service API:** This API can be used in atomic services since API version 15.|
| enableBackPressedEvent<sup>19+</sup>   | boolean | No  | Yes | Whether to support closing the ComponentContent under OverlayManager through a swipe gesture. The value **true** indicates yes, and **false** indicates no. The default value is **false**. <br>**Atomic service API:** This API can be used in atomic services since API version 19.|
| onBackPress   | [OnOverlayBackPressCallback](arkts-apis-uicontext-t.md#onoverlaybackpresscallback) | No  | Yes | Callback for intercepting the overlay swipe-back event.<br/>**NOTE**<br/>1. When this callback is registered and **enableBackPressedEvent** is set to **true**, the swipe-back event does not automatically close the overlay. Instead, this callback is invoked to determine whether the event is passed to lower-level components.<br/>2. The value **true** indicates that the event is intercepted (consumed and not passed to lower-level components), and **false** indicates that the event is not intercepted and will be passed through to lower-level components.<br/>**Since:** 26.0.0<br/>**Atomic service API:** This API can be used in atomic services since API version 26.0.0.|

## GestureTriggerInfo<sup>20+</sup>

Defines the information provided when a specific gesture callback is triggered.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type  | Read-Only  |   Optional   |Description      |
| ------ | ---- | ---------- |---------- |---------- |
| event | [GestureEvent](../apis-arkui/arkui-ts/ts-gesture-common.md#gestureevent)   |No |  No      |Gesture event object.|
| current | [GestureRecognizer](arkui-ts/ts-gesture-common.md#gesturerecognizer12)    |No |  No     |Gesture recognizer object. Detailed gesture information can be obtained from this object. However, avoid retaining this object locally as it may become invalid after the node is released.|
| currentPhase  | [GestureActionPhase](arkts-apis-uicontext-e.md#gestureactionphase20) |No |  No     | Phase of the gesture action callback.|
| node  | [FrameNode](js-apis-arkui-frameNode.md) |No  |  Yes  |Node that triggers the gesture. The default value is **null**, indicating that no specific node triggers the gesture.|

## GestureObserverConfigs<sup>20+</sup>

Specifies the gesture callback phases to listen for (passing an empty array means no gesture callback stage is listened for). Notifications are sent only when the gesture triggers the specified phases.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type  | Read-Only |  Optional      |Description      |
| ------ | ---- | ---------- |---------- |---------- |
| actionPhases | Array\<[GestureActionPhase](arkts-apis-uicontext-e.md#gestureactionphase20)\> | No | No | Gesture callback phases to listen for. An empty array is invalid. Notifications are sent only when the gesture triggers the specified phases. |

## SwiperContentInfo<sup>22+</sup>

Provides content area information of the **Swiper** component.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type| Read-Only | Optional| Description                   |
| --------- | ---- | ----- | ---- | ----------------------- |
| id        | string  | No| No| ID of the **Swiper** component.|
| uniqueId  | number  | No| No| Unique ID of the **Swiper** component.|
| swiperItemInfos   | Array\<[SwiperItemInfo](#swiperiteminfo22)\> | No| No| Information about the currently visible child components within the **Swiper** container.|

## SwiperItemInfo<sup>22+</sup>

Provides information about **Swiper** child components.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name     | Type| Read-Only | Optional| Description                   |
| --------- | ---- | ----- | ---- | -----------------------|
| uniqueId  | number | No| No| Unique ID of the **Swiper** child component.  |
| index     | number | No| No| Index of the child component in the **Swiper** container.|