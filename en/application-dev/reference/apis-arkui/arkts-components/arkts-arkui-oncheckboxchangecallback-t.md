# OnCheckboxChangeCallback

```TypeScript
declare type OnCheckboxChangeCallback = (value: boolean) => void
```

Represents the callback invoked when the selected state of the check box changes.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the check box is selected. The value **true** means that the check box is selected, and **false** means the opposite. |
