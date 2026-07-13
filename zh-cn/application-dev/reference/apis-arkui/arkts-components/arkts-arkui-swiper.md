# Swiper

滑块视图容器，提供子组件滑动轮播显示的能力。

> **说明：**

> - Swiper组件通过内置的[PanGesture]{@link gesture}拖动手势实现滑动轮播效果，将[disableSwipe]{@link SwiperAttribute#disableSwipe}属性设为true
> 时，会禁用该手势监听，从而阻止滑动操作。
>
> - Swiper中复用[NodeContainer]{@link node_container}时，禁止递归流程中子节点更新父节点状态变量。


## Swiper

```TypeScript
Swiper(controller?: SwiperController)
```

创建滑块视图容器。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| controller | SwiperController | 否 | 给组件绑定一个控制器，用来控制组件翻页或者预加载指定子节点。 |

## 汇总

- [ArrowStyle](arkts-arkui-swiper-arrowstyle-i.md)
- [AutoPlayOptions](arkts-arkui-swiper-autoplayoptions-i.md)
- [CachedCountOptions](arkts-arkui-swiper-cachedcountoptions-i.md)
- [IndicatorIconInfo](arkts-arkui-swiper-indicatoriconinfo-i.md)
- [IndicatorStyle](arkts-arkui-swiper-indicatorstyle-i.md)
- [SwiperAnimationEvent](arkts-arkui-swiper-swiperanimationevent-i.md)
- [SwiperAutoFill](arkts-arkui-swiper-swiperautofill-i.md)
- [SwiperContentAnimatedTransition](arkts-arkui-swiper-swipercontentanimatedtransition-i.md)
- [SwiperContentTransitionProxy](arkts-arkui-swiper-swipercontenttransitionproxy-i.md)
- [SwiperContentWillScrollResult](arkts-arkui-swiper-swipercontentwillscrollresult-i.md)
- [ContentDidScrollCallback](arkts-arkui-swiper-contentdidscrollcallback-t.md)
- [ContentWillScrollCallback](arkts-arkui-swiper-contentwillscrollcallback-t.md)
- [OnSwiperAnimationEndCallback](arkts-arkui-swiper-onswiperanimationendcallback-t.md)
- [OnSwiperAnimationStartCallback](arkts-arkui-swiper-onswiperanimationstartcallback-t.md)
- [OnSwiperGestureSwipeCallback](arkts-arkui-swiper-onswipergestureswipecallback-t.md)
- [SwiperAnimationMode](arkts-arkui-swiper-swiperanimationmode-e.md)
- [SwiperDisplayMode](arkts-arkui-swiper-swiperdisplaymode-e.md)
- [SwiperNestedScrollMode](arkts-arkui-swiper-swipernestedscrollmode-e.md)
