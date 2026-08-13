# ArrayListForEachCb

```TypeScript
export type ArrayListForEachCb<T> =  (value: T, index: int, arrlist: ArrayList<T>) => void
```

ArrayList中forEach方法的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ArrayListForEachCb<T> =  (value: T, index: int, arrlist: ArrayList<T>) => void--><!--Device-unnamed-export type ArrayListForEachCb<T> =  (value: T, index: int, arrlist: ArrayList<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前遍历到的元素。 |
| index | int | 是 | 当前遍历到的下标值。 |
| arrlist | [ArrayList](arkts-arkts-util-arraylist-arraylist-c.md)&lt;T&gt; | 是 | 当前调用forEach方法的实例对象。 |

