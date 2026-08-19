# OnScrollEdgeCallback

```TypeScript
declare type OnScrollEdgeCallback = (side: Edge) => void
```

滚动到边缘时触发的回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare type OnScrollEdgeCallback = (side: Edge) => void--><!--Device-unnamed-declare type OnScrollEdgeCallback = (side: Edge) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| side | Edge | 是 | 滚动到的边缘位置。竖直方向滚动时，Edge.Top和Edge.Start表示起始边缘，Edge.Bottom和Edge.End表示末尾边缘。水平方向滚动时，Edge.Center表示水平方 向起始位置，Edge.Baseline表示水平方向末尾位置。 |

