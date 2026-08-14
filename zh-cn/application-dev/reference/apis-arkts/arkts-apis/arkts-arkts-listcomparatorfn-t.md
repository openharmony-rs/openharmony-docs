# ListComparatorFn

```TypeScript
export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double
```

List中sort方法的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double--><!--Device-unnamed-export type ListComparatorFn<T> = (firstValue: T, secondValue: T) => double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstValue | T | 是 | 需要排序的前一项元素。 |
| secondValue | T | 是 | 需要排序的后一项元素。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 通过回调函数返回的值，List能够根据自定义的比较规则维护元素的顺序。 |

