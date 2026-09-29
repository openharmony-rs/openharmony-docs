# OnSubmitCallback

```TypeScript
declare type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void
```

Callback for submission.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void--><!--Device-unnamed-declare type OnSubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enterKey | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Enter key type of the input method. |
| event | [SubmitEvent](arkts-arkui-textinput-comp-submitevent-i.md) | Yes | Submit event. You can control whether to collapse the keyboard. |
