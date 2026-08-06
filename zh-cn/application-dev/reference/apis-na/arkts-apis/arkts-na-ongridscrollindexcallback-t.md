# OnGridScrollIndexCallback

```TypeScript
export type OnGridScrollIndexCallback = (first: int, last: int) => void
```

Grid组件可见区域item变化事件的回调类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnGridScrollIndexCallback = (first: int, last: int) => void--><!--Device-unnamed-export type OnGridScrollIndexCallback = (first: int, last: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | int | 是 | 当前显示的Grid起始位置的索引值。  |
| last | int | 是 | 当前显示的Grid终止位置的索引值。  |

