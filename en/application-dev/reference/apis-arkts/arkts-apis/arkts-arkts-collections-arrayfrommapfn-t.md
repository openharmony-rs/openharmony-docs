# ArrayFromMapFn

```TypeScript
type ArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType
```

Defines the ArkTS Array reduction function, which is used by the 'from' API of the Array class.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | FromElementType | Yes | Element that is being processed. |
| index | number | Yes | Index of the element in the ArkTS array. |

**Return value:**

| Type | Description |
| --- | --- |
| ToElementType | The transformed value. |
