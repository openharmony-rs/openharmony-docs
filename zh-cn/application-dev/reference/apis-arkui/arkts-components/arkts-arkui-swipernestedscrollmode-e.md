# SwiperNestedScrollMode

Swiper组件和父组件的嵌套滚动模式枚举。

**起始版本：** 11

<!--Device-unnamed-declare enum SwiperNestedScrollMode--><!--Device-unnamed-declare enum SwiperNestedScrollMode-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELF_ONLY

```TypeScript
SELF_ONLY = 0
```

Swiper只自身滚动，不与父组件联动。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperNestedScrollMode-SELF_ONLY = 0--><!--Device-SwiperNestedScrollMode-SELF_ONLY = 0-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## SELF_FIRST

```TypeScript
SELF_FIRST = 1
```

Swiper自身先滚动，自身滚动到边缘以后父组件滚动。父组件滚动到边缘以后，如果父组件有边缘效果，则父组件触发边缘效果，否则Swiper触发边缘效果。

**起始版本：** 11

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperNestedScrollMode-SELF_FIRST = 1--><!--Device-SwiperNestedScrollMode-SELF_FIRST = 1-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

