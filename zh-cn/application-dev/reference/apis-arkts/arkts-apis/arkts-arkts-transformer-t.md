# Transformer

```TypeScript
type Transformer = (this: Object, key: string, value: Object) => Object | undefined | null
```

定义转换结果函数的类型。

当作为[JSON.parse](arkts-arkts-parse-f.md#parse-1)的参数时，对象的每个成员都会调用此函数，可在解析期间进行自定义数据处理或转换。

当作为
[JSON.stringify](arkts-arkts-stringify-f.md#stringify-2)的参数时，
在序列化期间用于转换和处理每个属性。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| this | Object | 是 | 待解析键值对所属的对象。 |
| key | string | 是 | 待解析的键。 |
| value | Object | 是 | 键对应的值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Object \| undefined \| null | 返回Object、undefined或null值。 |

