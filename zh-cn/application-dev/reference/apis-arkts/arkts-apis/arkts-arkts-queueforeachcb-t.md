# QueueForEachCb

```TypeScript
export type QueueForEachCb<T> = (value: T, index: int, queue: Queue<T>) => void
```

Queue的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type QueueForEachCb<T> = (value: T, index: int, queue: Queue<T>) => void--><!--Device-unnamed-export type QueueForEachCb<T> = (value: T, index: int, queue: Queue<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前遍历到的元素。  |
| index | int | 是 | 当前遍历到的下标值。 该值为整数。  |
| queue | \_\_\_MD\_LINK\_USD\_0\_\_\_&lt;T&gt; | 是 | 当前正在遍历的Queue实例。  |

