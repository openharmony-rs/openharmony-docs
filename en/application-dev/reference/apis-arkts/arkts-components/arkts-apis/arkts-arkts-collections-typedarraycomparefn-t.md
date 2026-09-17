# TypedArrayCompareFn

```TypeScript
type TypedArrayCompareFn<ElementType> = (first: ElementType, second: ElementType) => number
```

Describes the sort function of the ArkTS typed array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| first | ElementType | Yes | First element to be compared. |
| second | ElementType | Yes | Second element to be compared. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The result of the comparison. |
