# DynamicNode

```TypeScript
declare class DynamicNode<T>
```

Define DynamicNode.

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

<a id="onmove-1"></a>

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
