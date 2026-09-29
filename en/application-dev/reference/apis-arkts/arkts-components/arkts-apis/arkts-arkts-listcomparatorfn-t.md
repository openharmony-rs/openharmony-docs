# ListComparatorFn

```TypeScript
export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => number
```

This type specifies the comparator of sort in comparation.

**Since:** 23

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-unnamed-export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double--><!--Device-unnamed-export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double-End-->

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| firstValue | T | Yes | firstValue (required) previous element. |
| secondValue | T | Yes | secondValue (required) next element. |

**Return value:**

| Type | Description |
| --- | --- |
| number | the number type |
