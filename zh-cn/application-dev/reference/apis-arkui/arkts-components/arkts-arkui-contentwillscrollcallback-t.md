# ContentWillScrollCallback

```TypeScript
declare type ContentWillScrollCallback = (result: SwiperContentWillScrollResult) => boolean
```

Swiper即将滑动前触发的回调，返回值表示是否允许此次滑动。

**起始版本：** 15

**模型约束：** 此接口仅可在Stage模型下使用。

**元服务API：** 从API版本15开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本15开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| result | SwiperContentWillScrollResult | 是 | 即将滑动的相关信息，主要包括：当前页面对应的index、滑动方向上即将显示的页面index和此次滑动的位移。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | Swiper是否响应本次滑动，true表示响应，false表示不响应。 |

