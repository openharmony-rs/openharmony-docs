# ValueType

```TypeScript
type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets | Float32Array | bigint
```

用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。

**起始版本：** 9

**ArkTS模式：** ArkTS-Dyn起始版本为9；ArkTS-Sta起始版本为23。

<!--Device-relationalStore-type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets | Float32Array | bigint--><!--Device-relationalStore-type ValueType = null | long | double | string | boolean | Uint8Array | Asset | Assets | Float32Array | bigint-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型 | 说明 |
| --- | --- |
| null | 表示值类型为空。 |
| long | 表示值类型为长整型。 |
| double | 表示值类型为双精度浮点型。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |
| Uint8Array | 表示值类型为Uint8类型的数组。 |
| Asset | 表示值类型为附件Asset。[since 10] |
| Assets | 表示值类型为附件数组Assets。[since 10] |
| Float32Array | 表示值类型为浮点数组。[since 12] |
| bigint | 表示值类型为任意长度的整数。[since 12] |

