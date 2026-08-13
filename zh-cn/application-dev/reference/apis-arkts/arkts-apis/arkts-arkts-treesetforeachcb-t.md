# TreeSetForEachCb

```TypeScript
export type TreeSetForEachCb<T> = (value: T, key: T, set: TreeSet<T>) => void
```

TreeSet的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type TreeSetForEachCb<T> = (value: T, key: T, set: TreeSet<T>) => void--><!--Device-unnamed-export type TreeSetForEachCb<T> = (value: T, key: T, set: TreeSet<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前元素的值。 |
| key | T | 是 | 当前元素的键（与value相同）。 |
| set | [TreeSet](arkts-arkts-util-treeset-treeset-c.md)&lt;T&gt; | 是 | 当前正在遍历的TreeSet实例。 |

