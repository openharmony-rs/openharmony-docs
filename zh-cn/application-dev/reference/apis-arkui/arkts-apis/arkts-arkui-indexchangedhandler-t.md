# IndexChangedHandler

```TypeScript
export type IndexChangedHandler = (index: int) => void
```

当前显示元素的索引变化时，告知应用。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type IndexChangedHandler = (index: int) => void--><!--Device-unnamed-export type IndexChangedHandler = (index: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| index | int | 是 | 当前显示元素的索引。index序列从0开始。  |

