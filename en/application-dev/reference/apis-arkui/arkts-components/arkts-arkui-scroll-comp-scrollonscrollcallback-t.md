# ScrollOnScrollCallback

```TypeScript
declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void
```

Represents the callback triggered when the **Scroll** component scrolls.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-unnamed-declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void--><!--Device-unnamed-declare type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xOffset | number | Yes | Horizontal offset relative to the previous frame. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp |
| yOffset | number | Yes | Vertical offset relative to the previous frame. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp |
| scrollState | [ScrollState](arkts-arkui-list-comp-scrollstate-e.md) | Yes | Current scroll state. Idle indicates the idle state, Scroll indicates the scrolling state, and Fling indicates the inertial scroll state. |
