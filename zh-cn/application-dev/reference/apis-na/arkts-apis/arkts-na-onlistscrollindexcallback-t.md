# OnListScrollIndexCallback

```TypeScript
export type OnListScrollIndexCallback = (start: int, end: int, center: int) => void
```

List组件可见区域item变化事件的回调类型。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnListScrollIndexCallback = (start: int, end: int, center: int) => void--><!--Device-unnamed-export type OnListScrollIndexCallback = (start: int, end: int, center: int) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | int | 是 | List显示区域内第一个子组件的索引值。  |
| end | int | 是 | List显示区域内最后一个子组件的索引值。  |
| center | int | 是 | List显示区域内中间位置子组件的索引值。  |

