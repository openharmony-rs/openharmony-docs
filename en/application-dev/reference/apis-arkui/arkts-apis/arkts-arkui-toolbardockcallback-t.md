# ToolBarDockCallback

```TypeScript
export declare type ToolBarDockCallback = (area: DockArea, direction: Axis) => void
```

工具栏停靠到指定区域和方向时的回调。

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

<!--Device-unnamed-export declare type ToolBarDockCallback = (area: DockArea, direction: Axis) => void--><!--Device-unnamed-export declare type ToolBarDockCallback = (area: DockArea, direction: Axis) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| area | [DockArea](arkts-arkui-arkui-advanced-toolbarcontainer-dockarea-e.md) | Yes | 工具栏停靠的区域。 |
| direction | [Axis](arkts-arkui-axis-e.md) | Yes | 停靠方向。 |
