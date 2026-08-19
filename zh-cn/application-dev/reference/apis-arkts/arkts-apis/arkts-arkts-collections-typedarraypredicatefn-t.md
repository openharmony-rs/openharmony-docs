# TypedArrayPredicateFn

```TypeScript
type TypedArrayPredicateFn<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => boolean
```

ArkTS TypedArray断言函数类型，被TypedArray类的'some'、'every'、'filter'、'find'和'findIndex'接口使用。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-collections-type TypedArrayPredicateFn<ElementType, ArrayType> =    (value: ElementType, index: number, array: ArrayType) => boolean--><!--Device-collections-type TypedArrayPredicateFn<ElementType, ArrayType> =    (value: ElementType, index: number, array: ArrayType) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ElementType | 是 | 当前遍历的ArkTS TypedArray元素，用于判断是否满足测试条件。 |
| index | number | 是 | 当前遍历的ArkTS TypedArray元素索引，从0开始。 |
| array | ArrayType | 是 | 当前遍历的ArkTS TypedArray实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 断言函数的结果，该结果作为判断当前元素是否通过测试条件。为true时表示当前元素已满足测试条件，为false时表示当前元素不满足测试条件。 |

