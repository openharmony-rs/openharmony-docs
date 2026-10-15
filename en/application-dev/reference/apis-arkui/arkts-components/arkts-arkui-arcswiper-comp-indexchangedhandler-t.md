# IndexChangedHandler

```TypeScript
declare type IndexChangedHandler = (index: number) => void
```

Notifies the app when the index of the currently displayed element changes. The index sequence starts from 0.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-unnamed-declare type IndexChangedHandler = (index: number) => void--><!--Device-unnamed-declare type IndexChangedHandler = (index: number) => void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the currently displayed element. The index is zero-based. |
