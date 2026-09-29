# OnItemDragStartCallback

```TypeScript
declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder
```

Called when a list or grid element starts to be dragged.

**Since:** 23

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-unnamed-declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder--><!--Device-unnamed-declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ItemDragInfo](arkts-arkui-common-comp-itemdraginfo-i.md) | Yes | Information about the drag point. |
| itemIndex | number | Yes | Index of the dragged element. |

**Return value:**

| Type | Description |
| --- | --- |
| [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | Returns a **CustomBuilder** object for constructing the drag preview of the dragged element. If **void** is returned, the drag operation cannot be performed. |
