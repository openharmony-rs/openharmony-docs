# ScrollOnWillScrollCallback

```TypeScript
declare type ScrollOnWillScrollCallback =
 (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | OffsetResult
```

Callback triggered before scrolling.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type ScrollOnWillScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | OffsetResult--><!--Device-unnamed-declare type ScrollOnWillScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | OffsetResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xOffset | number | Yes | Horizontal offset relative to the previous frame. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp |
| yOffset | number | Yes | Vertical offset relative to the previous frame. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp |
| scrollState | [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | Yes | Current scroll state. **Idle** indicates the idle state, **Scroll** indicates the scroll state, and **Fling** indicates the inertial scroll state. |
| scrollSource | [ScrollSource](../arkts-apis/arkts-arkui-scrollsource-e.md) | Yes | Source of the current scroll operation. **DRAG** indicates that the scroll is triggered by dragging, **FLING** indicates that the scroll is triggered by inertial sliding, **SCROLLER** indicates that the scroll is triggered by a Scroller method without animation, and **SCROLLER_ANIMATION** indicates that the scroll is triggered by a Scroller method with animation. |

**Return value:**

| Type | Description |
| --- | --- |
| void &#124; [OffsetResult](arkts-arkui-scroll-comp-offsetresult-i.md) | If **OffsetResult** is returned, the scrolling will be performed with the offsets specified. Otherwise, the scrolling will be performed with the offsets determined by **(xOffset, yOffset)**. |
