# Value

```TypeScript
declare type Value = boolean | number | Uint8Array
```

关键资产属性的内容，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md)的值。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务API中使用。

<!--Device-asset-declare type Value = boolean | number | Uint8Array--><!--Device-asset-declare type Value = boolean | number | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Asset

| 类型 | 说明 |
| --- | --- |
| boolean | The value is a boolean value, with a range of true or false. |
| number | The value is a number, and the value range is the enumerated value or number corresponding to the tag. |
| Uint8Array | The value is a byte array, and the content is defined by the service. |

