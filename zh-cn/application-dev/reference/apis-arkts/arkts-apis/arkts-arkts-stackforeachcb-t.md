# StackForEachCb

```TypeScript
export type StackForEachCb<T> = (value: T, index: int, stack: Stack<T>) => void
```

Stack的回调函数类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type StackForEachCb<T> = (value: T, index: int, stack: Stack<T>) => void--><!--Device-unnamed-export type StackForEachCb<T> = (value: T, index: int, stack: Stack<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前遍历到的元素。 |
| index | int | 是 | 当前遍历到的下标值。 该值为整数。 |
| stack | [Stack](arkts-arkts-util-stack-stack-c.md)&lt;T&gt; | 是 | 当前正在遍历的Stack实例。 |

