# CloudType（系统接口）

```TypeScript
type CloudType = null | number | number | string | boolean | Uint8Array | CloudAsset | CloudAssets
```

表示云数据字段可使用的类型。各接口参数的实际类型视其功能而定。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CloudSync.Server

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| null | The value is null. |
| long | The value is a 64-bit integer (int64_t). |
| double | The value is a floating-point number (float). |
| string | The value is a string. |
| boolean | The value is true or false. |
| Uint8Array | The value is a Uint8 array. |
| [CloudAsset](arkts-arkdata-cloudextension-cloudasset-i-sys.md) | The value is of the cloud asset type. |
| [CloudAssets](arkts-arkdata-cloudextension-cloudassets-t-sys.md) | The value is an array of cloud assets. |
