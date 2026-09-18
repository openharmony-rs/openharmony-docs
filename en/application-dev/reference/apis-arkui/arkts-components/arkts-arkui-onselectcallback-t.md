# OnSelectCallback

```TypeScript
declare type OnSelectCallback = (index: number, selectStr: string) => void
```

Defines the callback invoked when a drop-down menu option is selected.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the selected option. The index is zero-based. |
| selectStr | string | Yes | Value of the selected option. |
