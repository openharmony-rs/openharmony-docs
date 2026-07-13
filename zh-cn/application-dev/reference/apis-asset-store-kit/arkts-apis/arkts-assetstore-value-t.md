# Value

```TypeScript
declare type Value = boolean | number | Uint8Array
```

关键资产属性的内容，用作[AssetMap](arkts-assetstore-assetmap-t.md)的值。

**起始版本：** 11

**元服务API：** 从API版本14开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Security.Asset

| 类型 | 说明 |
| --- | --- |
| boolean | The value is a boolean value, with a range of true or false. |
| number | The value is a number, and the value range is the enumerated value or numbercorresponding to the tag. |
| Uint8Array | The value is a byte array, and the content is defined by the service. |

