# SwiperContentAnimatedTransition

Swiper自定义切换动画相关信息。

**起始版本：** 12

<!--Device-unnamed-declare interface SwiperContentAnimatedTransition--><!--Device-unnamed-declare interface SwiperContentAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: number
```

Swiper自定义切换动画超时时间。从页面执行默认动画（页面滑动）至移出视窗外的第一帧开始计时，如果到达该时间后，开发者仍未调用[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md)的finishTransition接口通知Swiper组件此页面的自定义动画已结束，那么组件就会认为此页面的自定义动画已结束，立即将该页面节点下渲染树。单位ms，默认值为0。

**类型：** number

**默认值：** 0 ms

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentAnimatedTransition-timeout?: number--><!--Device-SwiperContentAnimatedTransition-timeout?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<SwiperContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback&lt;SwiperContentTransitionProxy&gt;

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>--><!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

