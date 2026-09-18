# ValueType

```TypeScript
type ValueType = null | number | number | string | boolean | Uint8Array | Asset | Assets
```

Enumerates the value types, which vary with the parameter function.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CommonType

| Type | Description |
| --- | --- |
| null | The value is null. |
| long | The value is a 64-bit integer (int64_t). |
| double | The value is a floating-point number (float). |
| string | The value is a string. |
| boolean | The value is true or false. |
| Uint8Array | The value is an array of 8-bit unsigned integers. |
| [Asset](arkts-arkdata-commontype-asset-i.md) | The value is an instance of the Asset type. |
| [Assets](arkts-arkdata-commontype-assets-t.md) | The value is an instance of the Assets type. |
