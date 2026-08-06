# SwiperContentAnimatedTransition

Defines the swiper content animated transition options.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-export declare interface SwiperContentAnimatedTransition--><!--Device-unnamed-export declare interface SwiperContentAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## timeout

```TypeScript
timeout?: int
```

Swiper自定义切换动画超时时间。从页面执行默认动画（页面滑动）至移出视窗外的第一帧开始计时，如果到达该时间后，开发者仍未调用 [SwiperContentTransitionProxy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的finishTransition接口通知Swiper组件此页面的自定义动画已结束，那么组件就会认 为此页面的自定义动画已结束，立即将该页面节点下渲染树。单位：ms 单位为： ms，取值范围为全体整数，取值为undefined时，按默认值处理。 默认值： 0。

**类型：** int

**默认值：** 0 ms

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentAnimatedTransition-timeout?: int--><!--Device-SwiperContentAnimatedTransition-timeout?: int-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## transition

```TypeScript
transition: Callback<SwiperContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback&lt;SwiperContentTransitionProxy&gt;

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>--><!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

