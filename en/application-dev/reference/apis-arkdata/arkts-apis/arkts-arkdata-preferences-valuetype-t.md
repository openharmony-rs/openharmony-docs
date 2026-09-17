# ValueType

```TypeScript
type ValueType = number | string | boolean | Array<number> | Array<string> | Array<boolean> | Uint8Array | object | bigint
```

Enumerates the value types.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.DistributedDataManager.Preferences.Core

| Type | Description |
| --- | --- |
| number | The value is a number. |
| string | The value is a string. |
| boolean | The value is true or false. |
| Array&lt;number&gt; | The value is an array of numbers. |
| Array&lt;string&gt; | The value is an array of strings. |
| Array&lt;boolean&gt; | The value is a boolean array. |
| Uint8Array | The value is an array of 8-bit unsigned integers. [since 11] |
| object | The value is an object. [since 12] |
| bigint | The value is an integer in any format. [since 12] |
