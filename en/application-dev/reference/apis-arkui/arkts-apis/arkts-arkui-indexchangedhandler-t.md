# IndexChangedHandler

```TypeScript
declare type IndexChangedHandler = (index: number) => void
```

Defines the callback to notify the application when the index of the currently displayed element changes.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element. The index is zero-based. |
