# SwiperContentAnimatedTransition

ArcSwiper自定义切换动画相关信息。

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

<!--Device-unnamed-declare interface SwiperContentAnimatedTransition--><!--Device-unnamed-declare interface SwiperContentAnimatedTransition-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## timeout

```TypeScript
timeout?: number
```

ArcSwiper自定义切换动画超时时间。从页面执行默认动画（页面滑动）至移出视窗外的第一帧开始计时，如果到达该时间后，开发者仍未调用 [SwiperContentTransitionProxy]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_的 [finishTransition]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_接口通知ArcSwiper组件此页面的自定义动画已结束，组件将强制结束该页面的自定义动 画，并立即在该页面节点下渲染树。单位ms，默认值为0。

**类型：** number

**默认值：** 0 ms

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentAnimatedTransition-timeout?: number--><!--Device-SwiperContentAnimatedTransition-timeout?: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

## transition

```TypeScript
transition: Callback<SwiperContentTransitionProxy>
```

自定义切换动画具体内容。

**类型：** Callback&lt;SwiperContentTransitionProxy&gt;

**起始版本：** 18

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为18。

**原子化服务API：** 从API版本18开始，该接口支持在原子化服务API中使用。

<!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>--><!--Device-SwiperContentAnimatedTransition-transition: Callback<SwiperContentTransitionProxy>-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Circle

