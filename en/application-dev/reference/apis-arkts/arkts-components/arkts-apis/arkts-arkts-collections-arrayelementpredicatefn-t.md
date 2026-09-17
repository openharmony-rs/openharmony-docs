# ArrayElementPredicateFn

```TypeScript
type ArrayElementPredicateFn<ElementType> = (value: ElementType) => boolean
```

Defines the ArkTS Array predicate function, which is used by the 'retainAll'API of the Array class to determine whether array elements meet certain test conditions.

**Since:** 26.1.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.1.0.

**System capability:** SystemCapability.Utils.Lang

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | ElementType | Yes | Element that is being processed. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | True if the value meets the predicate, otherwise false. |
