# TextAreaSubmitCallback

```TypeScript
declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void
```

Called when the Enter key on the soft keyboard is pressed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-unnamed-declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void--><!--Device-unnamed-declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enterKeyType | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Type of the Enter key on the soft keyboard.<br>onSubmit is not triggered when the type is EnterKeyType.NEW_LINE. |
| event | [SubmitEvent](arkts-arkui-textinput-comp-submitevent-i.md) | No | Submit event, used to obtain the detailed information about the submit event. If this parameter is not passed in, the detailed information about the submit event cannot be obtained. |
