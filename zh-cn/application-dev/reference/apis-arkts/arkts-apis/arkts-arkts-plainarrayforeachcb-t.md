# PlainArrayForEachCb

```TypeScript
export type PlainArrayForEachCb<T> = (value: T, key: int, PlainArray: PlainArray<T>) => void
```

PlainArray的回调函数类型。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-export type PlainArrayForEachCb<T> = (value: T, key: int, PlainArray: PlainArray<T>) => void--><!--Device-unnamed-export type PlainArrayForEachCb<T> = (value: T, key: int, PlainArray: PlainArray<T>) => void-End-->

**系统能力：** SystemCapability.Utils.Lang

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| value | T | 是 | 当前元素的值。 |
| key | int | 是 | 当前元素的键。 该值为整数。 |
| PlainArray | [PlainArray](arkts-arkts-util-plainarray-plainarray-c.md)&lt;T&gt; | 是 | 当前正在遍历的PlainArray实例。 |

