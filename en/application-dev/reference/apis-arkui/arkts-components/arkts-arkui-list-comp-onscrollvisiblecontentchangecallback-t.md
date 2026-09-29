# OnScrollVisibleContentChangeCallback

```TypeScript
declare type OnScrollVisibleContentChangeCallback = (start: VisibleListContentInfo, end: VisibleListContentInfo) => void
```

Triggered when a child component enters or leaves the list display area.

Since API version 26.0.0, when **List** changes from having child components to being empty, the **index** member of the reported **start** and **end** parameters is **-1**, and the **itemGroupArea** and **itemIndexInGroup** members are **undefined**. Before API version 26.0.0, when **List** changes from having child components to being empty, the reported **start** and **end** parameters retain the values from the last time when there were child components.

If the values of **start** and **end** are both **0**, the **List** component contains only one child component.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 14.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type OnScrollVisibleContentChangeCallback = (start: VisibleListContentInfo, end: VisibleListContentInfo) => void--><!--Device-unnamed-declare type OnScrollVisibleContentChangeCallback = (start: VisibleListContentInfo, end: VisibleListContentInfo) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | [VisibleListContentInfo](arkts-arkui-list-comp-visiblelistcontentinfo-i.md) | Yes | 1. Index of the first child component in the list display area.<br>2. If the first child component in the list display area is **ListItemGroup**, you can obtain the area where the first child component belongs. <br>3. If the first child component in the list display area is **ListItem** in **ListItemGroup**, you can obtain the index of **ListItem** in **ListItemGroup**. |
| end | [VisibleListContentInfo](arkts-arkui-list-comp-visiblelistcontentinfo-i.md) | Yes | 1. Index of the last child component in the list display area.<br>2. If the last child component in the list display area is **ListItemGroup**, you can obtain the area where the last child component belongs. <br>3. If the last child component in the list display area is **ListItem** in **ListItemGroup**, you can obtain the index of **ListItem** in **ListItemGroup**. |
