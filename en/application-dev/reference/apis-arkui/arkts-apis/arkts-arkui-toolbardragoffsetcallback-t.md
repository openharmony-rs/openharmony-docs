# ToolBarDragOffsetCallback

```TypeScript
export declare type ToolBarDragOffsetCallback = (x: number, y: number) => void
```

相对于ToolBarContainer容器的拖拽偏移量回调。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-unnamed-export declare type ToolBarDragOffsetCallback = (x: number, y: number) => void--><!--Device-unnamed-export declare type ToolBarDragOffsetCallback = (x: number, y: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X轴偏移量，单位为vp。 |
| y | number | Yes | Y轴偏移量，单位为vp。 |
