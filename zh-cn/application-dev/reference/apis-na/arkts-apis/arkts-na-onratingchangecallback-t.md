# OnRatingChangeCallback

```TypeScript
export type OnRatingChangeCallback = (rating: double) => void
```

操作评分条的评星变化时触发该回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-export type OnRatingChangeCallback = (rating: double) => void--><!--Device-unnamed-export type OnRatingChangeCallback = (rating: double) => void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rating | double | 是 | 评分条的评分。 |

