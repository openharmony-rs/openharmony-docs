# TextAreaSubmitCallback

```TypeScript
declare type TextAreaSubmitCallback = (enterKeyType: EnterKeyType, event?: SubmitEvent) => void
```

Represents the callback invoked when the Enter key on the soft keyboard is pressed.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enterKeyType | [EnterKeyType](arkts-arkui-textinput-comp-enterkeytype-e.md) | Yes | Type of the Enter key.<br>If the type is **EnterKeyType.NEW_LINE**, **onSubmit** is not triggered. |
| event | [SubmitEvent](arkts-arkui-textinput-comp-submitevent-i.md) | No | Submit event. |
