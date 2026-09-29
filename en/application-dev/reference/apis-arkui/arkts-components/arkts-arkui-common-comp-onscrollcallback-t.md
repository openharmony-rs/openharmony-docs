# OnScrollCallback

```TypeScript
declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void
```

Triggered when the scrollable component scrolls.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 12.

<!--Device-unnamed-declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void--><!--Device-unnamed-declare type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scrollOffset | number | Yes | Offset relative to the previous frame. The offset is positive when the scrollable component is scrolled up and negative when it is scrolled down.<br>Unit: vp |
| scrollState | [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | Yes | Current scroll state. |
