# SubmitCallback

```TypeScript
declare type SubmitCallback = (enterKey: EnterKeyType, event: SubmitEvent) => void
```

Represents the callback invoked when the Enter key on the soft keyboard is pressed.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enterKey | [EnterKeyType](arkts-arkui-enterkeytype-e.md) | Yes | Type of the Enter key. For details, see **EnterKeyType**. |
| event | [SubmitEvent](arkts-arkui-submitevent-i.md) | Yes | Submit event, which provides a method to keep the component in editing state. When **EnterKeyType** is set to **NEW_LINE**, the editing state is retained by default. |
