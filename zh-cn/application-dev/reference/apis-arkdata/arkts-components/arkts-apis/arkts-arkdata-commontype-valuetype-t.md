# ValueType

```TypeScript
type ValueType = null | number | number | string | boolean | Uint8Array | Asset | Assets
```

表示允许的数据字段类型，接口参数具体类型根据其功能而定。

**起始版本：** 11

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 类型 | 说明 |
| --- | --- |
| null | 表示值类型为空。 |
| long | 表示值类型为数字。 |
| double | 表示值类型为数字。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |
| Uint8Array | 表示值类型为Uint8类型的数组。 |
| [Asset](arkts-arkdata-commontype-asset-i.md) | 表示值类型为附件[Asset](arkts-arkdata-commontype-asset-i.md)。 |
| [Assets](arkts-arkdata-commontype-assets-t.md) | 表示值类型为附件数组[Assets](arkts-arkdata-commontype-assets-t.md)。 |
