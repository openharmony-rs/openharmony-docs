# SwiperContentAnimatedTransition

ArcSwiper自定义切换动画相关信息。

**起始版本：** 18

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## timeout

```TypeScript
timeout?: number
```

ArcSwiper自定义切换动画超时时间。从页面执行默认动画（页面滑动）至移出视窗外的第一帧开始计时，如果到达该时间后，开发者仍未调用
[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md)的
[finishTransition](arkts-arkui-swipercontenttransitionproxy-i.md#finishtransition-1)接口通知ArcSwiper组件此页面的自定义动画已结束，那么组件就会认为此页面的自定义动
画已结束，立即在该页面节点下渲染树。单位ms，默认值为0。

**类型：** number

**默认值：** 0 ms

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## transition

```TypeScript
transition: Callback<SwiperContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback<SwiperContentTransitionProxy>

**起始版本：** 18

**元服务API：** 从API版本18开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

