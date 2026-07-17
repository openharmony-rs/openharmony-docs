# ValueType

```TypeScript
type ValueType = null | number | number | string | boolean | Uint8Array | Asset | Assets
```

用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。。

**起始版本：** 11

<!--Device-commonType-type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets--><!--Device-commonType-type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets-End-->

**系统能力：** SystemCapability.DistributedDataManager.CommonType

| 类型 | 说明 |
| --- | --- |
| null | 表示值类型为空。 |
| long | 表示值类型为数字。 |
| double | 表示值类型为数字。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |
| Uint8Array | 表示值类型为Uint8类型的数组。 |
| Asset | 表示值类型为附件Asset。 |
| Assets | 表示值类型为附件数组Assets。 |

