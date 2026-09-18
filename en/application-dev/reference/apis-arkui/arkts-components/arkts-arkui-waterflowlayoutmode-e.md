# WaterFlowLayoutMode

Enumerates the layout modes of the **WaterFlow** component.

**Since:** 12

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## ALWAYS_TOP_DOWN

```TypeScript
ALWAYS_TOP_DOWN = 0
```

Default layout mode where water flow items are arranged from top to bottom. Items in the viewport depend on the layout of all items above them. In cases of jumping to a position or switching column counts, the layout of all items above the must be recalculated.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## SLIDING_WINDOW

```TypeScript
SLIDING_WINDOW = 1
```

Sliding window mode. Only the layout information inside the viewport is considered, with no dependency on **FlowItem** components above the viewport. Hence, when jumping forward or switching column counts, only the **FlowItem** components within the viewport need to be laid out. This mode is recommended, especially when the application needs to support screen rotation or dynamic column‑count switching.

**NOTE:** 

1. During a non-animated redirection to a distant position, water flow items are laid out forward or backward based
on the target position. If the user then swipes back to the original position, the layout of the content may differ from before. This can lead to misalignment of the top nodes when a user swipes back to the top after the redirection. To counteract this issue, in this layout mode, the layout will be automatically adjusted after reaching the top of the viewport to ensure that the top is aligned. If there are multiple sections, adjustments will be made to the sections within the viewport when sliding ends.
2. The total offset returned by the currentOffset
or offset API of [scroller](arkts-arkui-waterflowoptions-i.md) is inaccurate after the jump or data update is triggered. The offset will be recalibrated when the user scrolls back to the top. The offset API is added in API version 23 and later versions.
3. If a jump action (for example, by calling [scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex)
without animation or [scrollEdge](arkts-arkui-scroller-c.md#scrolledge)) and an input offset (such as from a swipe gesture or a scrolling animation) are both initiated within the same frame, both will be executed.
4. If the [scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex) API is called without animation
to jump to a distant position (beyond the range of visible water flow items in the window), the total offset is calculated in the sliding window mode.
5. The [scrollBar](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#scrollbar11)
is supported only in API version 18 and later. In earlier versions, the scrollbar will not be displayed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full
