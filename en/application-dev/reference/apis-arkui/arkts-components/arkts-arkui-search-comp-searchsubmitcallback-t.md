# SearchSubmitCallback

```TypeScript
declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void
```

Callback invoked when the search icon or search button is tapped, or when the search button on the soft keyboard is pressed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-unnamed-declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void--><!--Device-unnamed-declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchContent | string | Yes | Text content entered in the current search box. |
| event | [SubmitEvent](arkts-arkui-textinput-comp-submitevent-i.md) | No | Submit event object, which can be used to keep the Search component in the editing state. If it is not passed in, the editing state cannot be kept. |
