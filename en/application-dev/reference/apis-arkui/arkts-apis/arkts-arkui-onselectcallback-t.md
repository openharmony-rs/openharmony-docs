# OnSelectCallback

```TypeScript
declare type OnSelectCallback = (index: number, selectValue: string) => void
```

Called when an item in the drop-down list box is selected.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the selected option. The index is zero-based. |
| selectValue | string | Yes | Value of the selected option. |
