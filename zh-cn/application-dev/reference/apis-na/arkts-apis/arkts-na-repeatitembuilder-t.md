# RepeatItemBuilder

```TypeScript
@Builder
type RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void
```

组件生成函数类型。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-@Buildertype RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void--><!--Device-unnamed-@Buildertype RepeatItemBuilder<T> = (repeatItem: RepeatItem<T>) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| repeatItem | [RepeatItem](arkts-na-repeat-repeatitem-i.md)&lt;T&gt; | 是 | 将item和index结合到一起的一个状态变量。 |

