# @ohos.arkui.dragController(DragController)

This module provides APIs for initiating drag actions. When receiving a gesture event, such as a touch or long-press event, an application can initiate a drag action and carry drag information therein.

> **NOTE:** 
> 
> - The functionality of this module depends on UI context. This means that the APIs of this module cannot be used where [the UI context is ambiguous](../../../ui/arkts-global-interface.md#ambiguous-ui-context). For details, see [UIContext](arkts-arkui-arkui-uicontext-uicontext-c.md).
> 
> - You can preview how this component looks on a real device, but not in DevEco Studio Previewer.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## Modules to Import

```TypeScript
import { dragController } from '@kit.ArkUI';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createDragAction](arkts-arkui-dragcontroller-createdragaction-f.md) | Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a promise to return the result. |
| [executeDrag](arkts-arkui-dragcontroller-executedrag-f.md#executedrag) | Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses an asynchronous callback to return the result. |
| [executeDrag](arkts-arkui-dragcontroller-executedrag-f.md#executedrag-1) | Initiates a drag action, with the object to be dragged and the drag information passed in. This API uses a promise to return the result. |
| [getDragPreview](arkts-arkui-dragcontroller-getdragpreview-f.md) | Obtains the **DragPreview** object, which represents the preview displayed during a drag operation. |

### Classes

| Name | Description |
| --- | --- |
| [DragPreview](arkts-arkui-dragcontroller-dragpreview-c.md) | Implements a **DragPreview** object. This API does not work in the **OnDrop** and **OnDragEnd** callbacks. |
| [SpringLoadingContext](arkts-arkui-dragcontroller-springloadingcontext-c.md) | Defines callback context information passed to applications during hover detection. It enables access to drag states, dynamic UI effect updates, and drag data for operation handling decisions. |

### Interfaces

| Name | Description |
| --- | --- |
| [AnimationOptions](arkts-arkui-dragcontroller-animationoptions-i.md) | Defines parameters related to drag-and-drop animation effects. |
| [DragAction](arkts-arkui-dragcontroller-dragaction-i.md) | Implements a **DragAction** object to subscribe to drag state changes and start the drag service. |
| [DragAndDropInfo](arkts-arkui-dragcontroller-draganddropinfo-i.md) | Provides the data reported when the state changes during dragging. |
| [DragEventParam](arkts-arkui-dragcontroller-drageventparam-i.md) | Callback used to return the result. |
| [DragInfo](arkts-arkui-dragcontroller-draginfo-i.md) | Defines the attributes required for initiating a drag action and information carried in the dragging process. |
| [DragSpringLoadingConfiguration](arkts-arkui-dragcontroller-dragspringloadingconfiguration-i.md) | Defines the configuration parameters for drag hover detection. The default settings typically suffice. These settings can be customized through [onDragSpringLoading](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondragspringloading) binding or dynamically updated during BEGIN state using [updateConfiguration](arkts-arkui-dragcontroller-springloadingcontext-c.md#updateconfiguration). |
| [SpringLoadingDragInfos](arkts-arkui-dragcontroller-springloadingdraginfos-i.md) | Defines the drag event information when hover detection is triggered. This API provides drag data summaries and additional drag event information, allowing applications to decide whether to respond to hover detection callbacks. |

### Enums

| Name | Description |
| --- | --- |
| [DragSpringLoadingState](arkts-arkui-dragcontroller-dragspringloadingstate-e.md) | Enumerates hover detection states during drag operations. Under default system configuration, if no CANCEL occurs, the state reporting is as follows: Hover still--&gt;500ms--&gt;BEGIN--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;UPDATE--&gt;100ms--&gt;END |
| [DragStartRequestStatus](arkts-arkui-dragcontroller-dragstartrequeststatus-e.md) | Enumerates the states defining whether an application can initiate a drag operation. This API is effective only when [onDragStart](../arkts-components/arkts-arkui-common-comp-commonmethod-c.md#ondragstart) is called. |
| [DragStatus](arkts-arkui-dragcontroller-dragstatus-e.md) | Describes the dragging start and end states. |
