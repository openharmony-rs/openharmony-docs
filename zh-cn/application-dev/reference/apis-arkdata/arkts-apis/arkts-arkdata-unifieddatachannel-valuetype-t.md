# ValueType

```TypeScript
type ValueType = number | number | number | string | boolean | image.PixelMap | Want | ArrayBuffer | object | null | undefined
```

用于表示统一数据记录允许的数据字段类型。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unifiedDataChannel-type ValueType = int | long | double | string | boolean | image.PixelMap | Want | ArrayBuffer | object | null | undefined--><!--Device-unifiedDataChannel-type ValueType = int | long | double | string | boolean | image.PixelMap | Want | ArrayBuffer | object | null | undefined-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

| 类型 | 说明 |
| --- | --- |
| int | 表示Int的类型。 |
| long | 表示Long的类型。 |
| double | 表示Double的类型。 |
| string | 表示string的类型。 |
| boolean | 表示boolean的类型。 |
| image.PixelMap | 表示[image.PixelMap]{ |
| Want | 表示[Want]{ |
| ArrayBuffer | 表示ArrayBuffer的类型。 |
| object | 表示object的类型。 |
| null | 表示null。 |
| undefined | 表示undefined。 |

