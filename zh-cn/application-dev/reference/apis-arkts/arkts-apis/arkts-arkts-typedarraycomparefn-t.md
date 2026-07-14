# TypedArrayCompareFn

```TypeScript
type TypedArrayCompareFn<ElementType> = (first: ElementType, second: ElementType) => number
```

ArkTS TypedArray排序函数类型。

**起始版本：** 12

**元服务API：** 从API版本12开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | ElementType | 是 | 当前待比较的第一个元素。 |
| second | ElementType | 是 | 当前待比较的第二个元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 元素比较的结果。如果`first`小于`second`，返回值为负数；如果`first`大于`second`，返回值为正数；如果两个值相等，返回值为0。 |

