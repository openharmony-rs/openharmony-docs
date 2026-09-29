# OnGetStartIndexByOffsetCallback (System API)

```TypeScript
declare type OnGetStartIndexByOffsetCallback = (totalOffset: number) => StartLineInfo
```

Calculates the start line position of the current page based on the total offset of the **Grid** component, which is used for fast scrolling or reverse scrolling. This callback must be set simultaneously with **onGetStartIndexByIndex** to take effect.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare type OnGetStartIndexByOffsetCallback = (totalOffset: double) => StartLineInfo--><!--Device-unnamed-declare type OnGetStartIndexByOffsetCallback = (totalOffset: double) => StartLineInfo-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| totalOffset | number | Yes | Total scrolling offset, that is, the offset between the top of the first **GridItem** in the **Grid** component and the top of the **Grid** component.<br>Unit:vp. |

**Return value:**

| Type | Description |
| --- | --- |
| [StartLineInfo](arkts-arkui-grid-comp-startlineinfo-i-sys.md) | Position of the start line in the grid. |
