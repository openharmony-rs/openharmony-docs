# OnGridScrollIndexCallback

```TypeScript
declare type OnGridScrollIndexCallback = (first: number, last: number) => void
```

Grid组件可见区域item变化事件的回调类型。

**起始版本：** 19

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本19开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnGridScrollIndexCallback = (first: number, last: number) => void--><!--Device-unnamed-declare type OnGridScrollIndexCallback = (first: number, last: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| first | number | 是 | 当前显示的Grid起始位置的索引值。  |
| last | number | 是 | 当前显示的Grid终止位置的索引值。  |

