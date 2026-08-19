# OnListScrollIndexCallback

```TypeScript
declare type OnListScrollIndexCallback = (start: number, end: number, center: number) => void
```

List组件可见区域item变化事件的回调类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本19开始，该接口支持在ArkTS卡片中使用。

<!--Device-unnamed-declare type OnListScrollIndexCallback = (start: number, end: number, center: number) => void--><!--Device-unnamed-declare type OnListScrollIndexCallback = (start: number, end: number, center: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| start | number | 是 | List显示区域内第一个子组件的索引值。 |
| end | number | 是 | List显示区域内最后一个子组件的索引值。 |
| center | number | 是 | List显示区域内中间位置子组件的索引值。 |

