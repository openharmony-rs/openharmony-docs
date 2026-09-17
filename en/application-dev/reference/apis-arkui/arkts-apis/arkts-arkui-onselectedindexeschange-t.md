# OnSelectedIndexesChange

```TypeScript
export type OnSelectedIndexesChange = (selectedIndexes: number[]) => void
```

Defines a callback invoked when the selected segmented button items change.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| selectedIndexes | number[] | Yes | Indexes of selected segmented button items. |
