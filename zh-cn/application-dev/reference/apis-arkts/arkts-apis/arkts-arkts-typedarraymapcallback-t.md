# TypedArrayMapCallback

```TypeScript
type TypedArrayMapCallback<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => ElementType
```

ArkTS TypedArray转换映射函数类型。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ElementType | 是 | 当前映射的ArkTS TypedArray元素。 |
| index | number | 是 | 当前映射的ArkTS TypedArray元素索引，从0开始。 |
| array | ArrayType | 是 | 当前映射的ArkTS TypedArray实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ElementType | 转换后的元素值。 |

