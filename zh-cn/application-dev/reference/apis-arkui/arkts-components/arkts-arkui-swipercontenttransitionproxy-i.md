# SwiperContentTransitionProxy

Swiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知Swiper组件页面自定义动画已结束。

**起始版本：** 12

<!--Device-unnamed-declare interface SwiperContentTransitionProxy--><!--Device-unnamed-declare interface SwiperContentTransitionProxy-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

<a id="finishtransition"></a>
## finishTransition

```TypeScript
finishTransition(): void
```

通知Swiper组件，此页面的自定义动画已结束。

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentTransitionProxy-finishTransition(): void--><!--Device-SwiperContentTransitionProxy-finishTransition(): void-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## index

```TypeScript
index: number
```

视窗内页面的索引。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentTransitionProxy-index: number--><!--Device-SwiperContentTransitionProxy-index: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## mainAxisLength

```TypeScript
mainAxisLength: number
```

index对应页面在主轴方向上的长度，单位vp。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentTransitionProxy-mainAxisLength: number--><!--Device-SwiperContentTransitionProxy-mainAxisLength: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## position

```TypeScript
position: number
```

index页面相对于Swiper主轴起始位置（selectedIndex对应页面的起始位置）的移动比例。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentTransitionProxy-position: number--><!--Device-SwiperContentTransitionProxy-position: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

## selectedIndex

```TypeScript
selectedIndex: number
```

当前选中页面的索引。

**类型：** number

**起始版本：** 12

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本12开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本26.0.0开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperContentTransitionProxy-selectedIndex: number--><!--Device-SwiperContentTransitionProxy-selectedIndex: number-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

