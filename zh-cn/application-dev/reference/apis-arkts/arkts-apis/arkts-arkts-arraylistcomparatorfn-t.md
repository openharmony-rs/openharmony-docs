# ArrayListComparatorFn

```TypeScript
export type ArrayListComparatorFn<T> = (firstValue: T, secondValue: T) => number
```

ArrayList中sort方法的比较器类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ArrayListComparatorFn<T> = (firstValue: T, secondValue: T) => double--><!--Device-unnamed-export type ArrayListComparatorFn<T> = (firstValue: T, secondValue: T) => double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstValue | T | 是 | 需要排序的前一项元素。 |
| secondValue | T | 是 | 需要排序的后一项元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | number类型。 |

