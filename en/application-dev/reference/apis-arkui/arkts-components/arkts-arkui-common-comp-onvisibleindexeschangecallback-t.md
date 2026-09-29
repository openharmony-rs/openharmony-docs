# OnVisibleIndexesChangeCallback

```TypeScript
declare type OnVisibleIndexesChangeCallback = (start: number, end: number) => void
```

Defines the callback type invoked when the indexes of the child components displayed by the lazy loading layout containers [LazyColumnLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazycolumnlayout.md), [LazyVGridLayout](arkts-arkui-lazyvgridlayout-comp.md), and [LazyVWaterFlowLayout](../../../reference/apis-arkui/arkui-ts/ts-container-lazyvwaterflowlayout.md) change.

> **NOTE:** 
> 
> - When the lazy loading layout container has no child components, both **start** and **end** return -1.
> 
> - When the lazy loading layout container has no child components in the visible area, both **start** and **end**return -1.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-unnamed-declare type OnVisibleIndexesChangeCallback = (start: int, end: int) => void--><!--Device-unnamed-declare type OnVisibleIndexesChangeCallback = (start: int, end: int) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| start | number | Yes | Index of the start position of the visible area.<br>Value range: [0, total number of child nodes - 1]. The value **-1** is returned when there is no child node or all child nodes are outside the visible area. |
| end | number | Yes | Index of the end position of the visible area.<br>Value range: [0, total number of child nodes - 1]. The value **-1** is returned when there is no child node or all child nodes are outside the visible area. |
