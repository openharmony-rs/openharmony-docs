# TypedArrayCompareFn

```TypeScript
type TypedArrayCompareFn<ElementType> = (first: ElementType, second: ElementType) => number
```

ArkTS TypedArray排序函数类型。

**起始版本：** 12

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为12。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-collections-type TypedArrayCompareFn<ElementType> = (first: ElementType, second: ElementType) => number--><!--Device-collections-type TypedArrayCompareFn<ElementType> = (first: ElementType, second: ElementType) => number-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | ElementType | 是 | 当前待比较的第一个元素。  |
| second | ElementType | 是 | 当前待比较的第二个元素。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 元素比较的结果。如果\_\_\_INLINE\_CODE\_USD\_0\_\_\_小于\_\_\_INLINE\_CODE\_USD\_1\_\_\_，返回值为负数；如果\_\_\_INLINE\_CODE\_USD\_2\_\_\_大于\_\_\_INLINE\_CODE\_USD\_3\_\_\_，返回值为正数；如果两个值相等，返回值为0。 |

