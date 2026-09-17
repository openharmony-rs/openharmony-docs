# OnGetStartIndexByOffsetCallback (System API)

```TypeScript
declare type OnGetStartIndexByOffsetCallback = (totalOffset: number) => StartLineInfo
```

Defines the callback type used in onGetStartIndexByOffset of GridLayoutOptions.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| totalOffset | number | Yes | Total scrolling offset, that is, the offset between the top of the first **GridItem** in the **Grid** component and the top of the **Grid** component.<br>Unit:vp. |

**Return value:**

| Type | Description |
| --- | --- |
| [StartLineInfo](arkts-arkui-startlineinfo-i-sys.md) | - |
