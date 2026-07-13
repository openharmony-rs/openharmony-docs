# OnRatingChangeCallback

```TypeScript
declare type OnRatingChangeCallback = (rating: number) => void
```

操作评分条的评星变化时触发该回调。

**起始版本：** 18

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rating | number | 是 | 评分条的评分。 |

