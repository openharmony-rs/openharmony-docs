# TypedArrayFromMapFn

```TypeScript
type TypedArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType
```

Describes the mapping function of the ArkTS typed array.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | FromElementType | Yes | Element that is currently traversed and used to construct an ArkTS typed array. |
| index | number | Yes | Index of the element. |

**Return value:**

| Type | Description |
| --- | --- |
| ToElementType | The transformed value. |
