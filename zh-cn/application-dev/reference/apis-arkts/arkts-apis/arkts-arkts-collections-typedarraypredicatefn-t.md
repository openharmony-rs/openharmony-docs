# TypedArrayPredicateFn

```TypeScript
type TypedArrayPredicateFn<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => boolean
```

ArkTS TypedArray断言测试函数类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-collections-type TypedArrayPredicateFn<ElementType, ArrayType> =    (value: ElementType, index: number, array: ArrayType) => boolean--><!--Device-collections-type TypedArrayPredicateFn<ElementType, ArrayType> =    (value: ElementType, index: number, array: ArrayType) => boolean-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ElementType | 是 | 当前遍历的ArkTS TypedArray元素。  |
| index | number | 是 | 当前遍历的ArkTS TypedArray元素索引，从0开始。  |
| array | ArrayType | 是 | 当前遍历的ArkTS TypedArray实例。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果值符合条件，则为true，否则为false。  |

