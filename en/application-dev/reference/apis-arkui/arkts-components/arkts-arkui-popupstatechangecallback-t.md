# PopupStateChangeCallback

```TypeScript
declare type PopupStateChangeCallback = (event: PopupStateChangeParam) => void
```

Represents the callback invoked when the popup state changes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [PopupStateChangeParam](arkts-arkui-popupstatechangeparam-i.md) | Yes | Display state of the popup. |
