# Transformer

```TypeScript
type Transformer = (this: Object, key: string, value: Object) => Object | undefined | null
```

Defines the type of the conversion result function.

When used as a parameter of [JSON.parse](arkts-arkts-json-parse-f.md), the function is called by each member of the object, allowing for custom data processing or conversion during parsing.

When used as a parameter of JSON.stringify, the function is used to transfer and handle each property during serialization.

**Since:** 12

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.Utils.Lang

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| this | Object | Yes | Object to which the key-value pair to parse belongs. |
| key | string | Yes | Key to parse. |
| value | Object | Yes | Value of the key. |

**Return value:**

| Type | Description |
| --- | --- |
| Object &#124; undefined &#124; null | Return an Object, undefined or null value |
