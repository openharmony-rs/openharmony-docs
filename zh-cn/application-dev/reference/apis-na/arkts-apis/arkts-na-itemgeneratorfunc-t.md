# ItemGeneratorFunc

```TypeScript
@Builder
declare type ItemGeneratorFunc<T> = (item: T, index: int) => void
```

Define item generator function.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Builderdeclare type ItemGeneratorFunc<T> = (item: T, index: int) => void--><!--Device-unnamed-@Builderdeclare type ItemGeneratorFunc<T> = (item: T, index: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| item | T | 是 | item in an array |
| index | int | 是 | index corresponding to an array item. 取值限定为整数。 |

