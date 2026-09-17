# ScrollOnWillScrollCallback

```TypeScript
declare type ScrollOnWillScrollCallback =
 (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | OffsetResult
```

Called before scroll to allow developer to control real offset the Scroll can scroll.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| xOffset | number | Yes | Horizontal offset per frame during scrolling. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp |
| yOffset | number | Yes | offset per frame during scrolling. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp |
| scrollState | [ScrollState](arkts-arkui-scrollstate-e.md) | Yes | Current scrolling state. |
| scrollSource | [ScrollSource](../arkts-apis/arkts-arkui-scrollsource-e.md) | Yes | Source of the current scrolling operation. |

**Return value:**

| Type | Description |
| --- | --- |
| void &#124; [OffsetResult](arkts-arkui-offsetresult-i.md) | the remain offset for the Scroll, same as (xOffset, yOffset) when no OffsetResult is returned. |
