# TypedArrayReduceCallback

```TypeScript
type TypedArrayReduceCallback<AccType, ElementType, ArrayType> =
    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType
```

Describes the reduce function of the ArkTS typed array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| previousValue | AccType | Yes | Accumulated value of the current traversal. |
| currentValue | ElementType | Yes | Element that is being traversed in the ArkTS typed array. |
| currentIndex | number | Yes | Index of the element. |
| array | ArrayType | Yes | ArkTS typed array that is being traversed. |

**Return value:**

| Type | Description |
| --- | --- |
| AccType | The result of the reduction. |
