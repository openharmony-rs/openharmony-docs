# OnGetStartIndexByIndexCallback (System API)

```TypeScript
declare type OnGetStartIndexByIndexCallback = (targetIndex: number) => StartLineInfo
```

Defines the callback type used in onGetStartIndexByIndex of GridLayoutOptions.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| targetIndex | number | Yes | The target index to scroll to. |

**Return value:**

| Type | Description |
| --- | --- |
| [StartLineInfo](arkts-arkui-startlineinfo-i-sys.md) | - |
