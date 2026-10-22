# DynamicNode

```TypeScript
declare class DynamicNode<T>
```

Define DynamicNode.

Drag sorting is used to implement manual sorting of list items or grid items, and is applicable to scenarios where users need to customize the order of items, such as to-do list sorting and playlist management. By using ForEach/LazyForEach/Repeat within a List or Grid component and setting the onMove event, drag sorting can be enabled when each iteration generates a ListItem or GridItem. After the drag is released, if the data position changes, the onMove event is triggered to report the start index and target index of the data movement. In the onMove event, the data source must be modified based on the reported start index and target index. Ensure that only the order of the data changes so that the placement animation can be executed properly.

> **NOTE:** 
> 
> - Supported since API version 12. If new content is added in later versions,
> - a superscript is used to mark the earliest API version of the content.
> 
> - Since API version 26.0.0, Grid supports onMove drag sorting. Currently,
> - Grid supports onMove drag sorting only in scrollable scenarios.
> - When a Grid contains GridItems spanning rows and columns,
> - if the next GridItem to be placed cannot fully fit in the current row,
> - the system searches downward row by row until it can be placed.
> - Therefore, when drag sorting is performed in a Grid with GridItems spanning rows and columns,
> - the new layout after dragging may contain some gaps.
> - You can drag again to adjust the GridItem positions to fill the gaps.
> 
> - When setting nodes spanning rows and columns in a Grid,
> - use [GridLayoutOptions](ts-container-grid.md#gridlayoutoptions10).
> - In the onMove event, the application should synchronously modify the corresponding irregular node information
> - to keep it consistent with the new layout after dragging.
> - For details, see
> - [Example 4](#example-4-using-foreach-onmove-for-drag-sorting-in-grid-irregular-layout-and-setting-the-drag-event-callback),
> - [Example 5](#example-5-using-lazyforeach-onmove-for-drag-sorting-in-grid-irregular-layout-and-setting-the-drag-event-callback)
> - ,and [Example 6](#example-6-using-repeats-onmove-for-drag-sorting-in-grid-irregular-layout-and-setting-the-drag-event-callback).
> 
> - The APIs of this module can be used only in the stage model.

**Since:** 12

<!--Device-unnamed-declare class DynamicNode<T>--><!--Device-unnamed-declare class DynamicNode<T>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>): T
```

Callback for data movement during drag sorting. It takes effect only when the parent container component is [List](arkts-arkui-list-comp.md) or [Grid](arkts-arkui-grid-comp.md) and each iteration of ForEach/LazyForEach/Repeat generates a ListItem or GridItem component. After being called, the drag sorting feature is enabled. After the drag is released, if the data position changes, the handler callback is triggered to report the start index and target index of the data movement. The data source must be modified in the callback, and it must be ensured that only the order of the data changes so that the placement animation can be executed properly.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>): T--><!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnMoveHandler](arkts-arkui-common-comp-onmovehandler-t.md)&gt; | Yes | Callback for data movement during drag sorting. Triggered when the data position changes due to dragging. In the callback, modify the data source based on the start index and target index. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |

## onMove

```TypeScript
onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T
```

Callback for data movement during drag sorting. It takes effect only when the parent container component is [List](arkts-arkui-list-comp.md) or [Grid](arkts-arkui-grid-comp.md) and each iteration of ForEach/LazyForEach/Repeat generates a ListItem or GridItem component. After being called, the drag sorting feature is enabled. After the drag is released, if the data position changes, the handler callback is triggered to report the start index and target index of the data movement. The data source must be modified in the callback, and it must be ensured that only the order of the data changes so that the placement animation can be executed properly. Compared with [onMove](#onmove), this API adds the eventHandler parameter, which can listen to drag phase events such as long press, drag start, passing over other components, and drag end.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T--><!--Device-DynamicNode-onMove(handler: Optional<OnMoveHandler>, eventHandler: ItemDragEventHandler): T-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnMoveHandler](arkts-arkui-common-comp-onmovehandler-t.md)&gt; | Yes | Callback for drag sorting data movement. Invoked when the data position changes due to dragging. In the callback, modify the data source based on the start index and target index. |
| eventHandler | [ItemDragEventHandler](arkts-arkui-common-comp-itemdrageventhandler-i.md) | Yes | Set of drag event callbacks, used to listen for drag phase events such as long press, drag start, passing over other components, and drag end. |

**Return value:**

| Type | Description |
| --- | --- |
| T | Current component. |
