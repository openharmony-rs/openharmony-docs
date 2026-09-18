# TypedArrayPredicateFn

```TypeScript
type TypedArrayPredicateFn<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => boolean
```

Describes the assertion function of the ArkTS typed array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | ElementType | Yes | Element that is being traversed in the ArkTS typed array. |
| index | number | Yes | Index of the element. |
| array | ArrayType | Yes | ArkTS typed array that is being traversed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if the value meets the predicate, otherwise false. |
