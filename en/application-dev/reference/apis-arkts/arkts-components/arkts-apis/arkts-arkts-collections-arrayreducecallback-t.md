# ArrayReduceCallback

```TypeScript
type ArrayReduceCallback<AccType, ElementType, ArrayType> =
    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType
```

Defines the ArkTS Array reduction function, which is used by the 'reduceRight' API of the Array class.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| previousValue | AccType | Yes | Accumulated value of the current traversal. |
| currentValue | ElementType | Yes | Element that is being traversed in the ArkTS array. |
| currentIndex | number | Yes | Index of the element in the ArkTS array. |
| array | ArrayType | Yes | ArkTS array that is being traversed. |

**Return value:**

| Type | Description |
| --- | --- |
| AccType | The result of the reduction. |
