# TreeSetComparator

```TypeScript
export type TreeSetComparator<T> = (firstValue: T, secondValue: T) => double
```

TreeSet的比较器类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type TreeSetComparator<T> = (firstValue: T, secondValue: T) => double--><!--Device-unnamed-export type TreeSetComparator<T> = (firstValue: T, secondValue: T) => double-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| firstValue | T | 是 | 第一个比较值。 |
| secondValue | T | 是 | 第二个比较值。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 比较结果。 |

