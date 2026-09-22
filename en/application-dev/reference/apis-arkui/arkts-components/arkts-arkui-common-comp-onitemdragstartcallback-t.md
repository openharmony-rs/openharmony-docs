# OnItemDragStartCallback

```TypeScript
declare type OnItemDragStartCallback = (event: ItemDragInfo, itemIndex: number) => CustomBuilder
```

Defines the callback type used in onItemDragStart.

**Since:** 23

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ItemDragInfo](arkts-arkui-common-comp-itemdraginfo-i.md) | Yes | Information about the dragged item. |
| itemIndex | number | Yes | The index number of the dragged item. |

**Return value:**

| Type | Description |
| --- | --- |
| [CustomBuilder](arkts-arkui-common-comp-custombuilder-t.md) | - |
