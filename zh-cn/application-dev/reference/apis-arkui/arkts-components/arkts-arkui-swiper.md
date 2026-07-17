# Swiper

滑块视图容器，提供子组件滑动轮播显示的能力。

> **说明：**

> - Swiper组件通过内置的[PanGesture]{@link gesture}拖动手势实现滑动轮播效果，将[disableSwipe]{@link SwiperAttribute#disableSwipe}属性设为true
> 时，会禁用该手势监听，从而阻止滑动操作。
>
> - Swiper中复用[NodeContainer]{@link node_container}时，禁止递归流程中子节点更新父节点状态变量。

## 子组件

可以包含子组件。

> **说明：**  
>  
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)、  
> [ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)、  
> [LazyForEach](docroot://ui/rendering-control/arkts-rendering-control-lazyforeach.md)和  
> [Repeat](docroot://ui/rendering-control/arkts-new-rendering-control-repeat.md)）。不建议子组件中混用懒加载组件（包括LazyForEach、Repeat  
> ）和非懒加载组件，或者子组件中使用多个懒加载组件，否则可能导致懒加载组件预加载能力失效等问题。不建议在组件动画过程中对数据源进行操作，否则会导致布局出现异常。  
>  
> - Swiper子组件的[visibility]{@link CommonMethod#visibility}属性设置为Visibility.None，且Swiper的displayCount属性设置为'auto'时，对应子组件在  
> 视窗内不占位，但不影响导航点个数；visibility属性设置为Visibility.None或者Visibility.Hidden时，对应子组件不显示，但依然会在视窗内占位。  
>  
> - 当Swiper子组件设置了[offset]{@link CommonMethod#offset}属性时，会按照子组件的层级进行绘制，层级高的子组件会覆盖层级低的子组件。例如，Swiper包含3个子组件，其中第3个子组件设置了  
> offset({ x : 100 })，那么在横向循环滑动中，第3个子组件会覆盖第1个子组件，此时可设置第1个子组件的[zIndex]{@link CommonMethod#zIndex}属性值大于第3个子组件，使第1个子组件层级  
> 高于第3个子组件。  
>  
> - 在走焦到用户定义的子节点时，导航点、箭头会由于[焦点样式](docroot://ui/arkts-common-events-focus-event.md#焦点样式)修改zIndex的行为被遮挡。  
>  
> - 在包含大量子组件的场景中，建议采用懒加载、缓存数据、预加载数据和组件复用等方法，以优化Swiper的性能并减少内存占用。最佳实践请参考  
> [优化Swiper组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-swiper_high_performance_development_guide)。  
>

## Swiper

```TypeScript
Swiper(controller?: SwiperController)
```

创建滑块视图容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

<!--Device-SwiperInterface-(controller?: SwiperController): SwiperAttribute--><!--Device-SwiperInterface-(controller?: SwiperController): SwiperAttribute-End-->

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
