# ValueType

```TypeScript
type ValueType = null | number | string | boolean | Uint8Array | Asset | Assets
```

Enumerates the data field types, which are determined by API parameter functions.

**Since:** 11

<!--Device-commonType-type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets--><!--Device-commonType-type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets-End-->

**System capability:** SystemCapability.DistributedDataManager.CommonType

| Type | Description |
| --- | --- |
| null | The value is null. |
| long | The value is a 64-bit integer (int64_t). |
| double | The value is a floating-point number (float). |
| string | The value is a string. |
| boolean | The value is true or false. |
| Uint8Array | The value is a Uint8 array. |
| [Asset](arkts-arkdata-commontype-asset-i.md) | The value is an Asset. |
| [Assets](arkts-arkdata-commontype-assets-t.md) | The value is an array of Assets. |
