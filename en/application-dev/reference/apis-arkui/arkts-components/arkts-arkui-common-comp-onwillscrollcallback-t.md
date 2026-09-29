# OnWillScrollCallback

```TypeScript
declare type OnWillScrollCallback =
(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult
```

Triggered when the scrollable component is about to scroll.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type OnWillScrollCallback =(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult--><!--Device-unnamed-declare type OnWillScrollCallback =(scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scrollOffset | number | Yes | Offset relative to the previous frame. The offset is positive when the scrollable component is scrolled up and negative when it is scrolled down.<br>Unit: vp |
| scrollState | [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | Yes | Current scroll state. |
| scrollSource | [ScrollSource](../arkts-apis/arkts-arkui-scrollsource-e.md) | Yes | Source of the current scrolling operation. |

**Return value:**

| Type | Description |
| --- | --- |
| void &#124; [ScrollResult](arkts-arkui-common-comp-scrollresult-c.md) | Returns a **ScrollResult** object if the scrollable component scrolls by the developer-specified offset relative to the previous frame; returns no **ScrollResult** object if the component scrolls by the offset specified by **scrollOffset** in the callback.<br>Value range: (-∞, +∞) |
