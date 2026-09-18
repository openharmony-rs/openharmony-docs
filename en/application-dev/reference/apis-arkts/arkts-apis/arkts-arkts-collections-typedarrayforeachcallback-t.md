# TypedArrayForEachCallback

```TypeScript
type TypedArrayForEachCallback<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => void
```

Describes the traversal function of the ArkTS typed array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | ElementType | Yes | Element that is being traversed in the ArkTS typed array. |
| index | number | Yes | Index of the element. |
| array | ArrayType | Yes | ArkTS typed array that is being traversed. |
