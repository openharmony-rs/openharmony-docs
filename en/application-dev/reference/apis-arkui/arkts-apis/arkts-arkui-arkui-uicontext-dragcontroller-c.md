# DragController

Provides APIs for initiating drag actions. When receiving a gesture event, such as a touch or long-press event, an application can initiate a drag action and carry drag information therein.

> **NOTE:** 
> 
> In the following API examples, you must first use [getDragController()](arkts-arkui-arkui-uicontext-uicontext-c.md#getdragcontroller) in
> **UIContext** to obtain a **DragController** instance, and then call the APIs using the obtained instance.

**Since:** 11

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { AtomicServiceBar, ComponentUtils, ContextMenuController, CursorController, DialogPresenter, DragController, Font, KeyboardAvoidMode, MediaQuery, OverlayManager, PromptAction, Router, UIContext, UIInspector, UIObserver, PageInfo, SwiperDynamicSyncScene, SwiperDynamicSyncSceneType, MarqueeDynamicSyncScene, MarqueeDynamicSyncSceneType, MeasureUtils, FrameCallback, OverlayManagerOptions, TargetInfo, TextMenuController, NodeIdentity, NodeRenderState, NodeRenderStateChangeCallback, Magnifier, ResolvedUIContext, TextSelectionClearPolicy, CustomKeyboardContinueFeature, BackgroundLuminanceSamplingConfigs, LuminanceSampler } from '@kit.ArkUI';
import { GestureListenerType, GestureActionPhase, GestureTriggerInfo, GestureObserverConfigs, GestureListenerCallback } from '@kit.ArkUI';
import { SwiperContentInfo, SwiperItemInfo } from '@kit.ArkUI';
import { BackPressActionProposal, BaseGestureHandlingProposal, ClickActionProposal, GestureHandlingResolution, NoneActionProposal, PageSwitchActionProposal, ScrollActionProposal, SelectActionProposal, SmartGestureController, TargetedGestureProposal } from '@kit.ArkUI';
```

## cancelDataLoading

```TypeScript
cancelDataLoading(key: string): void
```

Cancels the data loading initiated by the [startDataLoading](../arkts-components/arkts-arkui-dragevent-i.md#startdataloading) API. This API can be called only after the drag is released.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Identifier for the drag data. It is used to distinguish between different drag operations. The key can be obtained through the **startDataLoading** API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [190004](../errorcode-drag-event.md#190004-operation-failed) | Operation failed. |

## createDragAction

```TypeScript
createDragAction(customArray: Array<CustomBuilder | DragItemInfo>, dragInfo: dragController.DragInfo): dragController.DragAction
```

Creates a drag action object for initiating drag and drop operations. You need to explicitly specify one or more drag previews, the drag data, and the drag handle point. If a drag operation initiated by an existing drag action object is not completed, no new object can be created, and calling the API will throw an exception. After the lifecycle of the drag action object ends, the callback functions registered on this object become invalid. Therefore, it is necessary to hold this object within a longer scope and replace the old value with a new object returned by **createDragAction** before each drag initiation.

> **NOTE:** 
> 
> For optimal drag and drop performance, limit the number of drag previews.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| customArray | Array&lt;[CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md)&gt; | Yes | Object to be dragged. |
| dragInfo | [dragController.DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| [dragController.DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | **DragAction** object, which is used to subscribe to drag state changes and start the drag service. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

## enableDropDisallowedBadge

```TypeScript
enableDropDisallowedBadge(enabled: boolean): void
```

Specifies whether to enable the display of a disallowed badge when dragged content is incompatible with a component's configured [allowDrop](../arkts-components/arkts-arkui-commonmethod-c.md#allowdrop) types. When a component can accept or process dragged data or returns **DragBehavior.COPY** to indicate copy mode processing, the drag preview shows a plus icon with data count badge. When the component returns **DragBehavior.MOVE** to indicate cut mode processing, only the data count badge appears. When this feature is enabled, the system automatically displays a disallowed badge during drag operations if the dragged data types are incompatible with the target component's allowed drop types. This API currently does not support [UIExtension](arkts-arkui-arkui-uiextension.md).

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable the display of a disallowed badge when dragged content is incompatible with a component's configured [allowDrop](../arkts-components/arkts-arkui-commonmethod-c.md#allowdrop) types. The value **true** means to enable the display of a disallowed badge, and **false** means the opposite. The default value is **false**. |

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo,
    callback: AsyncCallback<dragController.DragEventParam>): void
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a callback to return the drag event result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md) | Yes | Object to be dragged.<br> **NOTE:** <br>The global builder is not supported. If the [Image](../../apis-image-kit/arkts-apis/arkts-image-multimedia-image.md) component is used in the builder, enable synchronous loading, that is, set the syncLoad attribute of the component to **true**. The builder is used only to generate the image displayed during the current dragging. If the root component of the builder has zero width or height, it will cause failure in drag image generation, which in turn breaks the entire drag operation. Changes to the builder, if any, apply to the next dragging, but not to the current dragging. |
| dragInfo | [dragController.DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[dragController.DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | Yes | Callback used to return the result.<br>- **event**: drag event information that includes only the drag result.<br>- **extraParams**: extra information about the drag event.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

## executeDrag

```TypeScript
executeDrag(custom: CustomBuilder | DragItemInfo, dragInfo: dragController.DragInfo)
    : Promise<dragController.DragEventParam>
```

Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a promise to return the drag event result.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| custom | [CustomBuilder](../arkts-components/arkts-arkui-custombuilder-t.md) &#124; [DragItemInfo](../arkts-components/arkts-arkui-dragiteminfo-i.md) | Yes | Object to be dragged. |
| dragInfo | [dragController.DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Yes | Drag information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;{ event: DragEvent, extraParams: string }&gt; | Callback used to return the result.<br>- **event**: drag event information that includes only the drag result. <br>- **extraParams**: extra information about the drag event.<br>**Since:** 11 |
| Promise&lt;[dragController.DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md)&gt; | A Promise with the drag event information.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100001](../errorcode-internal.md#100001-internal-error) | Internal handling failed. |

## getDragPreview

```TypeScript
getDragPreview(): dragController.DragPreview
```

Obtains the **DragPreview** object, which represents the preview displayed during a drag operation.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [dragController.DragPreview](arkts-arkui-dragcontroller-dragpreview-c.md) | **DragPreview** object. It provides the API for setting the preview style. It does not work in the **OnDrop** and **OnDragEnd** callbacks. |

## notifyDragStartRequest

```TypeScript
notifyDragStartRequest(requestStatus: dragController.DragStartRequestStatus): void
```

Controls whether the application can initiate a drag operation.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| requestStatus | [dragController.DragStartRequestStatus](arkts-arkui-dragcontroller-dragstartrequeststatus-e.md) | Yes | Whether the application can initiate a drag operation. |

## setDragEventStrictReportingEnabled

```TypeScript
setDragEventStrictReportingEnabled(enable: boolean): void
```

Sets whether the **onDragLeave** callback of the parent component is triggered when an item is dragged from the parent to the child component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether the **onDragLeave** callback of the parent component is triggered when an item is dragged from the parent to the child component. The value **true** means the **onDragLeave** callback of the parent component is triggered, and **false** means the opposite. |
