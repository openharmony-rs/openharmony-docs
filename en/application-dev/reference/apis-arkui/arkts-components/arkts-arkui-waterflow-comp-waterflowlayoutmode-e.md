# WaterFlowLayoutMode

```TypeScript
declare enum WaterFlowLayoutMode
```

Enumerates the layout modes of the **WaterFlow** component.

| Comparison Item| ALWAYS_TOP_DOWN (Default)| SLIDING_WINDOW |  
|---------|------------------------|----------------|  
| Applicable scenario | Fixed number of columns | Dynamic number of columns, large data volume, and screen rotation |  
| Layout policy| Complete layout from the top| Sliding window layout|  
| Performance| Depends on all flow items above.| Only considers the layout in the viewport|  
| Jump efficiency| Calculates all layouts above| Quick jump without complete calculation|  
| Column-count switching| Recalculates all layouts.| Re-lays out only the content in the viewport|  
| Screen rotation| Supported, but poor performance| Supported with good performance|  
| Scrollbar display| Always supported| Supported in API version 18 and later|  
| Layout consistency| Always consistent| May be inconsistent after jump|

**Since:** 12

<!--Device-unnamed-declare enum WaterFlowLayoutMode--><!--Device-unnamed-declare enum WaterFlowLayoutMode-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_TOP_DOWN

```TypeScript
ALWAYS_TOP_DOWN = 0
```

Default layout mode where water flow items are arranged from top to bottom. Items in the viewport depend on the layout of all items above them. In cases of jumping to a position or switching column counts, the layout of all items above the viewport must be recalculated.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WaterFlowLayoutMode-ALWAYS_TOP_DOWN = 0--><!--Device-WaterFlowLayoutMode-ALWAYS_TOP_DOWN = 0-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDING_WINDOW

```TypeScript
SLIDING_WINDOW = 1
```

Moving-window layout mode. Only the layout information within the viewport is considered, and there is no dependency on the flow items above the viewport. Therefore, when jumping backward or switching the number of columns, only the flow items within the viewport need to be laid out. It is recommended to use this mode preferentially, especially in scenarios where the app needs to support screen rotation or dynamically switch the number of columns.

**NOTE:** 

  1. When jumping to a distant position without animation, flow items are laid out forward or backward
based on the target position. After that, if you slide back to the position before the jump, the layout effect of the content may be inconsistent with the previous one. This effect may cause the top nodes to be misaligned when sliding back to the top after the jump.
  2. When the **SLIDING_WINDOW** layout mode is used and [WaterFlowSections](arkts-arkui-waterflow-comp-waterflowsections-c.md)
groups are set, after the scrolling animation ends, if the viewport contains the start position of a group and it is detected that the column or row start position of the group within the viewport is not aligned, or the start **FlowItem** of the group is inconsistent with the group start index, **WaterFlow** recalculates the layout to correct the group content position.
  3. When the **SLIDING_WINDOW** layout mode is used and backToTop
is called to return to the top, if the top is still not reached after the return-to-top animation ends, **WaterFlow** performs a top correction without animation to realign the content to the start position.
  4. The total offset returned by the [currentOffset](arkts-arkui-scroll-comp-scroller-c.md#currentoffset)
or [offset](arkts-arkui-scroll-comp-scroller-c.md#offset) API of [scroller](arkts-arkui-waterflow-comp-waterflowoptions-i.md) is inaccurate after a jump or data update is triggered, and is recalibrated when sliding back to the top. Since API version 23, the offset API is added.
  5. If a jump (such as [scrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex) or [scrollEdge](arkts-arkui-scroll-comp-scroller-c.md#scrolledge)
without animation) and an input offset (such as a sliding gesture or scrolling animation) are called within the same frame, both take effect.
  6. When [scrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex) without animation is called to jump,
if the jump is to a distant position (a position exceeding the number of flow items within the viewport), the moving-window mode estimates the total offset.
  7. The scrollbar
[scrollBar](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbar11) display is supported only in API version 18 and later. In earlier versions, the scrollbar is not displayed even if it is set.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WaterFlowLayoutMode-SLIDING_WINDOW = 1--><!--Device-WaterFlowLayoutMode-SLIDING_WINDOW = 1-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full
