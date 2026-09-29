# OnMoveHandler

```TypeScript
declare type OnMoveHandler = (from: number, to: number) => void
```

Defines the callback triggered when data is moved during drag-and-drop sorting.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type OnMoveHandler = (from: number, to: number) => void--><!--Device-unnamed-declare type OnMoveHandler = (from: number, to: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| from | number | Yes | Start index of the drag operation. The value range is [0, data source length - 1]. |
| to | number | Yes | End index of the drag operation. The value range is [0, data source length - 1]. |
