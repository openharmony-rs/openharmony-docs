# SearchSubmitCallback

```TypeScript
declare type SearchSubmitCallback = (searchContent: string, event?: SubmitEvent) => void
```

Called when the search icon, search button, or soft keyboard search button is clicked.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchContent | string | Yes | Current text input. |
| event | [SubmitEvent](arkts-arkui-submitevent-i.md) | No | Submit event. |
