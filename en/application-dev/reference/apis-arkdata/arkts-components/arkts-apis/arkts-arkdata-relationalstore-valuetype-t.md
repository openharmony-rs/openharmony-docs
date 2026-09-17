# ValueType

```TypeScript
type ValueType = null | number | number | string | boolean | Uint8Array | Asset | Assets | Float32Array | bigint
```

Indicates possible value types

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

| Type | Description |
| --- | --- |
| null | The value is a null |
| long | The value is a long |
| double | The value is a double |
| string | The value is a string |
| boolean | The value is a boolean |
| Uint8Array | The value is an array of the Uint8 |
| [Asset](arkts-arkdata-relationalstore-asset-i.md) | The value is an asset [since 10] |
| [Assets](arkts-arkdata-relationalstore-assets-t.md) | The value is an array of the asset [since 10] |
| Float32Array | The value is an array of the float32 [since 12] |
| bigint | The value is an integer of any length [since 12] |
