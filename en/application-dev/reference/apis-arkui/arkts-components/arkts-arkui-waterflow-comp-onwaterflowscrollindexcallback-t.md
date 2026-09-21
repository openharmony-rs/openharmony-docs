# OnWaterFlowScrollIndexCallback

```TypeScript
declare type OnWaterFlowScrollIndexCallback = (first: number, last: number) => void
```

Represents a callback for item changes in the visible area of the **WaterFlow** component.

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| first | number | Yes | Index of the first item of the component. |
| last | number | Yes | Index of the last item of the component. |
