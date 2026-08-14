# HashSetCbFn

```TypeScript
export type HashSetCbFn<T> = (value: T, key: T, set: HashSet<T>) => void
```

HashSet中forEach方法的回调函数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type HashSetCbFn<T> = (value: T, key: T, set: HashSet<T>) => void--><!--Device-unnamed-export type HashSetCbFn<T> = (value: T, key: T, set: HashSet<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前遍历到的元素值，forEach遍历过程中总会传入此参数。 |
| key | T | 是 | 当前遍历到的元素值（与value相同），forEach遍历过程中总会传入此参数。 |
| set | [HashSet](arkts-arkts-util-hashset-hashset-c.md)&lt;T&gt; | 是 | 当前调用forEach方法的实例对象。 |

