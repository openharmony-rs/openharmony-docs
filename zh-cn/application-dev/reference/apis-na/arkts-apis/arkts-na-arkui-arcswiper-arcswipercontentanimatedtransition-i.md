# ArcSwiperContentAnimatedTransition

ArcSwiper自定义切换动画相关信息。

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-export declare interface ArcSwiperContentAnimatedTransition--><!--Device-unnamed-export declare interface ArcSwiperContentAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## timeout

```TypeScript
timeout?: int
```

ArcSwiper自定义切换动画超时时间。从页面执行默认动画（页面滑动）至移出视窗外的第一帧开始计时，如果到达该时间后，开发者仍未调用 SwiperContentTransitionProxy 的[finishTransition](arkts-na-arkui-arcswiper-arcswipercontenttransitionproxy-i.md#finishTransition)接口通知ArcSwiper组件此页面的自定义动画已结束，那么组件就会认为此页面的 自定义动画已结束，立即在该页面节点下渲染树。&lt;br/&gt;单位：ms&lt;br/&gt;默认值：0。

**类型：** int

**默认值：** 0ms

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperContentAnimatedTransition-timeout?: int--><!--Device-ArcSwiperContentAnimatedTransition-timeout?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## transition

```TypeScript
transition: Callback<ArcSwiperContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback&lt;[ArcSwiperContentTransitionProxy](arkts-na-arkui-arcswiper-arcswipercontenttransitionproxy-i.md)&gt;

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为26.0.0。

**废弃版本：** -1

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-ArcSwiperContentAnimatedTransition-transition: Callback<ArcSwiperContentTransitionProxy>--><!--Device-ArcSwiperContentAnimatedTransition-transition: Callback<ArcSwiperContentTransitionProxy>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

