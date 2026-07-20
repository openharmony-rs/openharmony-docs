# ListComparatorFn

```TypeScript
export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => number
```

List排序比较器的类型。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double--><!--Device-unnamed-export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstValue | T | 是 | firstValue（必填）前一项元素。  |
| secondValue | T | 是 | secondValue（必填）后一项元素。  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 数值类型。  |

