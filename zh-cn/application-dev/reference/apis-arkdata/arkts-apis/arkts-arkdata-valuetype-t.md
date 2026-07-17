# ValueType

```TypeScript
export type ValueType = number | number | string | boolean
```

该类型用于表示数据库允许的数据字段类型。

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本20开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ValueType = long | double | string | boolean--><!--Device-unnamed-export type ValueType = long | double | string | boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

| 类型 | 说明 |
| --- | --- |
| long | [since 20] |
| double | [since 20] |
| string | The value is a string. [since 12] |
| boolean | The value is **true** or **false**. [since 12] |

