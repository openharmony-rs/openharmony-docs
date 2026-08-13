# ValueType

```TypeScript
type ValueType = long | double | string | boolean | Array<long> | Array<double> | Array<string> | Array<boolean>
    | Uint8Array | RecordData | bigint
```

Indicates possible value types

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

<!--Device-preferences-type ValueType = long | double | string | boolean | Array<long> | Array<double> | Array<string> | Array<boolean>    | Uint8Array | RecordData | bigint--><!--Device-preferences-type ValueType = long | double | string | boolean | Array<long> | Array<double> | Array<string> | Array<boolean>    | Uint8Array | RecordData | bigint-End-->

**系统能力：** 
- API版本23+：SystemCapability.DistributedDataManager.Preferences.Core

| 类型 | 说明 |
| --- | --- |
| long | 表示值类型为long类型数字。 |
| double | 表示值类型为double类型数字。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |
| Array&lt;long&gt; | 表示值类型为数字类型的数组。 |
| Array&lt;double&gt; | 表示值类型为数字类型的数组。 |
| Array&lt;string&gt; | 表示值类型为字符串类型的数组。 |
| Array&lt;boolean&gt; | 表示值类型为布尔类型的数组。 |
| Uint8Array | 表示值类型为8位无符号整型的数组。 |
| RecordData | 表示值类型为RecordData。 |
| bigint | 表示值类型为任意精度格式的整数。 |

