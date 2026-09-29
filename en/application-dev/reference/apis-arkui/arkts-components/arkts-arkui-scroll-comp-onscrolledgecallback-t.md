# OnScrollEdgeCallback

```TypeScript
declare type OnScrollEdgeCallback = (side: Edge) => void
```

Represents the callback triggered when scrolling reaches an edge.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnScrollEdgeCallback = (side: Edge) => void--><!--Device-unnamed-declare type OnScrollEdgeCallback = (side: Edge) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| side | [Edge](../arkts-apis/arkts-arkui-edge-e.md) | Yes | Edge position to scroll to. In vertical scroll, **Edge.Top** and **Edge.Start** indicate the start edge, and **Edge.Bottom** and **Edge.End** indicate the end edge. In horizontal scroll, **Edge.Center** indicates the start position in the horizontal direction, and **Edge.Baseline** indicates the end position in the horizontal direction. |
