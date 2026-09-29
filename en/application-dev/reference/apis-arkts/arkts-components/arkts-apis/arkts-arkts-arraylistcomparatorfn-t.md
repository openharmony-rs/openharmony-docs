# ArrayListComparatorFn

```TypeScript
export type ArrayListComparatorFn<T> = (firstValue: T, secondValue: T) => number
```

This type specifies the comparator of sort in comparation.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API (ArkTS-Dyn only) :** This API can be used in atomic services since version 23.

<!--Device-unnamed-export type ArrayListComparatorFn<T> = (firstValue: T, secondValue: T) => double--><!--Device-unnamed-export type ArrayListComparatorFn<T> = (firstValue: T, secondValue: T) => double-End-->

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
