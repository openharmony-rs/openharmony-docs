# TypedArrayReduceCallback

```TypeScript
type TypedArrayReduceCallback<AccType, ElementType, ArrayType> =
    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType
```

ArkTS TypedArray归约函数类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-collections-type TypedArrayReduceCallback<AccType, ElementType, ArrayType> =
    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType--><!--Device-collections-type TypedArrayReduceCallback<AccType, ElementType, ArrayType> =
    (previousValue: AccType, currentValue: ElementType, currentIndex: number, array: ArrayType) => AccType-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| previousValue | AccType | 是 | 当前遍历所累积的值。  |
| currentValue | ElementType | 是 | 当前遍历的ArkTS TypedArray元素。  |
| currentIndex | number | 是 | 当前遍历的ArkTS TypedArray元素索引，从0开始。  |
| array | ArrayType | 是 | 当前遍历的ArkTS TypedArray实例。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| AccType | 归约函数的结果。该结果会作为下一次调用TypedArrayReduceCallback时的previousValue参数。  |

