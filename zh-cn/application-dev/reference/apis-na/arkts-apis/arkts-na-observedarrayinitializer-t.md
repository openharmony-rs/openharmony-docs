# ObservedArrayInitializer

```TypeScript
type ObservedArrayInitializer<T> = (index: int) => T
```

ObservedArray的元素初始化函数类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-type ObservedArrayInitializer<T> = (index: int) => T--><!--Device-unnamed-type ObservedArrayInitializer<T> = (index: int) => T-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 当前初始化元素的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| T | 对应索引位置的元素值。 |

