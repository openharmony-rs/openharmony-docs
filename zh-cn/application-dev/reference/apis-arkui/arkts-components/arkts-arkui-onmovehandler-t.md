# OnMoveHandler

```TypeScript
declare type OnMoveHandler = (from: number, to: number) => void
```

定义数据源拖拽回调。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnMoveHandler = (from: number, to: number) => void--><!--Device-unnamed-declare type OnMoveHandler = (from: number, to: number) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| from | number | 是 | 数据源拖拽起始索引号。取值范围是[0, 数据源长度-1]。 |
| to | number | 是 | 数据源拖拽目标索引号。取值范围是[0, 数据源长度-1]。 |

