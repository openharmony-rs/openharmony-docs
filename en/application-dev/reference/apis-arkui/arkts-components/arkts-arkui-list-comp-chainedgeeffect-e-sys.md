# ChainEdgeEffect (System API)

```TypeScript
declare enum ChainEdgeEffect
```

Sets the edge effect of the chain animation effect, which determines how the spacing between list items changes when the list continues to be dragged after being scrolled to the edge.

**Since:** 10

<!--Device-unnamed-declare enum ChainEdgeEffect--><!--Device-unnamed-declare enum ChainEdgeEffect-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## DEFAULT

```TypeScript
DEFAULT
```

Default effect. When the list continues to be dragged after scrolling to the edge, the spacing between list items in the drag direction decreases,

and the spacing between list items in the opposite direction increases. This is suitable for scenarios that require directional stretching and rebound feedback.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainEdgeEffect-DEFAULT--><!--Device-ChainEdgeEffect-DEFAULT-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

## STRETCH

```TypeScript
STRETCH
```

When the list continues to be dragged after scrolling to the edge, the spacing between all list items increases. This is suitable for scenarios that require synchronous stretching feedback of all list items.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

<!--Device-ChainEdgeEffect-STRETCH--><!--Device-ChainEdgeEffect-STRETCH-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.
