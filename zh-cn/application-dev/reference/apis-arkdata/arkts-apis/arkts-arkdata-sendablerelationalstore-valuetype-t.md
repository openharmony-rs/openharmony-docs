# ValueType

```TypeScript
type ValueType = null | number | string | boolean | collections.Uint8Array | Asset | Assets |
    collections.Float32Array | bigint
```

用于表示允许的数据字段类型，接口参数具体类型根据其功能而定。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

<!--Device-sendableRelationalStore-type ValueType = null | number | string | boolean | collections.Uint8Array | Asset | Assets |    collections.Float32Array | bigint--><!--Device-sendableRelationalStore-type ValueType = null | number | string | boolean | collections.Uint8Array | Asset | Assets |    collections.Float32Array | bigint-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

| 类型 | 说明 |
| --- | --- |
| null | 表示值类型为空。 |
| number | 表示值类型为数字。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |
| collections.Uint8Array | 表示值类型为Uint8类型的数组。 |
| Asset | 表示值类型为附件Asset。\_\_\_HTML\_TAG\_USD\_0\_\_\_当字段类型是Asset时，在创建表的SQL语句中，类型应当为：ASSET。 |
| Assets | 表示值类型为附件数据集合Assets。\_\_\_HTML\_TAG\_USD\_0\_\_\_当字段类型是Assets时，在创建表的SQL语句中，类型应当为：ASSETS。 |
| collections.Float32Array | 表示值类型为浮点数组。\_\_\_HTML\_TAG\_USD\_0\_\_\_当字段类型是collections.Float32Array时，在创建表的SQL语句中，类型应当为： floatvector(128)。 |
| bigint | 表示值类型为任意长度的整数。\_\_\_HTML\_TAG\_USD\_1\_\_\_当字段类型是bigint时，在创建表的SQL语句中，类型应当为：UNLIMITED INT，详见 \_\_\_MD\_LINK\_USD\_0\_\_\_。\_\_\_HTML\_TAG\_USD\_2\_\_\_**说明：** \_\_\_HTML\_TAG\_USD\_3\_\_\_bigint类型字段不能比较大小，不适用以下谓词操作：between、notBetween、greaterThan、lessThan、greaterThanOrEqualTo、lessThanOrEqualTo、 orderByAsc、orderByDesc。\_\_\_HTML\_TAG\_USD\_4\_\_\_bigint类型字段的数据写入时，需通过BigInt()方法或在数据尾部添加'n'的方式明确为bigint类型，如'let data = BigInt(1234)'或 'let data = 1234n'。\_\_\_HTML\_TAG\_USD\_5\_\_\_bigint字段如果写入number类型的数据，则查询该数据的返回类型为number，而非bigint。 |

