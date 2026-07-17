# TypedArrayFromMapFn

```TypeScript
type TypedArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType
```

ArkTS TypedArray映射函数类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-collections-type TypedArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType--><!--Device-collections-type TypedArrayFromMapFn<FromElementType, ToElementType> = (value: FromElementType, index: number) => ToElementType-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | FromElementType | 是 | 当前遍历的用于构造ArkTS TypedArray的元素。 |
| index | number | 是 | 当前遍历的用于构造ArkTS TypedArray的元素索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ToElementType | 转换后的元素值。 |

