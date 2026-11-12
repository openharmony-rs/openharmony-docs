# Value

```TypeScript
declare type Value = boolean | number | Uint8Array
```

关键资产属性的内容，用作[AssetMap](arkts-assetstore-asset-assetmap-t.md)的值。

**起始版本：** 11

**原子化服务API：** 从API版本14开始，该接口支持在原子化服务中使用。

<!--Device-asset-declare type Value = boolean | number | Uint8Array--><!--Device-asset-declare type Value = boolean | number | Uint8Array-End-->

**系统能力：** SystemCapability.Security.Asset

| 类型 | 说明 |
| --- | --- |
| boolean | 表示值类型为布尔类型，取值为true或false。 |
| number | 表示值类型为数字，取值为枚举值或对应Tag支持的数字。 |
| Uint8Array | 表示值类型为字节数组，内容由业务定义。 |
