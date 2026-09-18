# ArrayPredicateFn

```TypeScript
type ArrayPredicateFn<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => boolean
```

Defines the ArkTS Array reduction function, which is used by the 'some' and 'every'APIs of the Array class to determine whether array elements meet certain test conditions.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | ElementType | Yes | Element that is being processed. |
| index | number | Yes | Index of the element in the ArkTS array. |
| array | ArrayType | Yes | ArkTS array that is being traversed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if the value meets the predicate, otherwise false. |
