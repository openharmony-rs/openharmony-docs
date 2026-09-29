# OnGetStartIndexByIndexCallback (System API)

```TypeScript
declare type OnGetStartIndexByIndexCallback = (targetIndex: number) => StartLineInfo
```

Calculates the start line on the page when the grid is scrolled to the specified target index. This API is used to support operations such as [scrollToIndex](Scroller#scrollToIndex). This callback must be set simultaneously with **onGetStartIndexByOffset** to take effect.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo--><!--Device-unnamed-declare type OnGetStartIndexByIndexCallback = (targetIndex: int) => StartLineInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetIndex | number | Yes | Index of the target **GridItem** to be scrolled to. |

**Return value:**

| Type | Description |
| --- | --- |
| [StartLineInfo](arkts-arkui-grid-comp-startlineinfo-i-sys.md) | Position of the start line in the grid. |
