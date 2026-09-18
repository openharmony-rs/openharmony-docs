# ValueType（系统接口）

```TypeScript
type ValueType = number | number | number | string | boolean | Uint8Array | null
```

用于表示允许的数据字段类型，接口参数的具体类型根据其功能而定。

**起始版本：** 22

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

| 类型 | 说明 |
| --- | --- |
| int | 表示值类型为数字，可取整型。 |
| long | 表示值类型为数字，可取长整型。 |
| double | 表示值类型为数字，可取小数。 |
| string | 表示值类型为字符串。 |
| boolean | 表示值类型为布尔值。 |
| Uint8Array | 表示值类型为Uint8类型的数组。 |
| null | 表示值类型为空。 |
