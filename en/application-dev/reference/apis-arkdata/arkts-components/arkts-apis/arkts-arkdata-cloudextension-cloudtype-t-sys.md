# CloudType (System API)

```TypeScript
type CloudType = null | number | number | string | boolean | Uint8Array | CloudAsset | CloudAssets
```

Enumerates the types of the cloud data field. The specific type is determined by the parameter function.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Server

**System API:** This is a system API.

| Type | Description |
| --- | --- |
| null | The value is null. |
| long | The value is a 64-bit integer (int64_t). |
| double | The value is a floating-point number (float). |
| string | The value is a string. |
| boolean | The value is true or false. |
| Uint8Array | The value is a Uint8 array. |
| [CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md) | The value is of the cloud asset type. |
| [CloudAssets](arkts-arkdata-cloudextension-cloudassets-t-sys.md) | The value is an array of cloud assets. |
