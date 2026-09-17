# OnDidChangeCallback

```TypeScript
declare type OnDidChangeCallback = (rangeBefore: TextRange, rangeAfter: TextRange) => void
```

Represents the callback invoked after text changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rangeBefore | [TextRange](arkts-arkui-textrange-i.md) | Yes | Range of the text to be changed. |
| rangeAfter | [TextRange](arkts-arkui-textrange-i.md) | Yes | Range of the text added. |
