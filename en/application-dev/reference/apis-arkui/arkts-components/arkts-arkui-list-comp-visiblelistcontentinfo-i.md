# VisibleListContentInfo

```TypeScript
declare interface VisibleListContentInfo
```

Describes the details of the child components in the visible area of a list.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

Index of the list item or list item group in the list display area.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemGroupArea

```TypeScript
itemGroupArea?: ListItemGroupArea
```

Position of the top or bottom edge of the viewport in the list item group to which the edge is located, if applicable.

**Type:** [ListItemGroupArea](arkts-arkui-list-comp-listitemgrouparea-e.md)

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## itemIndexInGroup

```TypeScript
itemIndexInGroup?: number
```

Index of the starting or ending list item in the list item group to which the top or bottom edge of the viewport is located.

**Type:** number

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
