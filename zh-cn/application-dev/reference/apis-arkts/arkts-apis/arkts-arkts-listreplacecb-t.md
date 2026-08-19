# ListReplaceCb

```TypeScript
export type ListReplaceCb<T> = (value: T, index: int, list: List<T>) => T
```

List的回调函数类型。

**起始版本：** 23

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type ListReplaceCb<T> = (value: T, index: int, list: List<T>) => T--><!--Device-unnamed-export type ListReplaceCb<T> = (value: T, index: int, list: List<T>) => T-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前元素的旧值。 |
| index | int | 是 | 当前元素的下标。 该值为整数。 |
| list | [List](arkts-arkts-util-list-list-c.md)&lt;T&gt; | 是 | 当前正在遍历的List实例。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 当前元素的新值。 |

