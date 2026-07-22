# TypedArrayForEachCallback

```TypeScript
type TypedArrayForEachCallback<ElementType, ArrayType> =
    (value: ElementType, index: number, array: ArrayType) => void
```

ArkTS TypedArray遍历函数类型。

**起始版本：** 12

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-collections-type TypedArrayForEachCallback<ElementType, ArrayType> =    (value: ElementType, index: number, array: ArrayType) => void--><!--Device-collections-type TypedArrayForEachCallback<ElementType, ArrayType> =    (value: ElementType, index: number, array: ArrayType) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | ElementType | 是 | 当前遍历的ArkTS TypedArray元素。  |
| index | number | 是 | 当前遍历的ArkTS TypedArray元素索引，从0开始。  |
| array | ArrayType | 是 | 当前遍历的ArkTS TypedArray实例。  |

