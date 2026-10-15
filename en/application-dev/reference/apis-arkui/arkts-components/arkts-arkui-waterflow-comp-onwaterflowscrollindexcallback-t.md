# OnWaterFlowScrollIndexCallback

```TypeScript
declare type OnWaterFlowScrollIndexCallback = (first: number, last: number) => void
```

Represents a callback for item changes in the visible area of the **WaterFlow** component.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-unnamed-declare type OnWaterFlowScrollIndexCallback = (first: number, last: number) => void--><!--Device-unnamed-declare type OnWaterFlowScrollIndexCallback = (first: number, last: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| first | number | Yes | Index of the start position of the currently displayed WaterFlow.<br>Normal value range: [0, total child components - 1]. When the list is empty, special values apply. For details, see [onScrollIndex](arkts-arkui-waterflow-comp-attribute.md#onscrollindex). |
| last | number | Yes | Index of the end position of the currently displayed WaterFlow.<br>Normal value range: [0, total child components - 1]. When the list is empty, special values apply. For details, see [onScrollIndex](arkts-arkui-waterflow-comp-attribute.md#onscrollindex). |
