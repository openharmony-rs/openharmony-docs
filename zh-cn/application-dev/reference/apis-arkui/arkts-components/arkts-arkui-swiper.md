# Swiper

滑块视图容器，提供子组件滑动轮播显示的能力。适用于轮播图展示、图片浏览、引导页、卡片轮播等场景。 > **说明：** > - Swiper组件通过内置的PanGesture拖动手势实现滑动轮播效果，将disableSwipe属性设为true > 时，会禁用该手势监听，从而阻止滑动操作。 > > - Swiper中复用NodeContainer时，禁止递归流程中子节点更新父节点状态变量。

## 子组件 可以包含子组件。 > **说明：** > > - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、 > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、 > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和 > [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）。不建议子组件中混用懒加载组件（包括LazyForEach、Repeat > ）和非懒加载组件，或者子组件中使用多个懒加载组件，否则可能导致懒加载组件预加载能力失效等问题。不建议在组件动画过程中对数据源进行操作，否则会导致布局出现异常。 > > - Swiper子组件的visibility属性设置为Visibility.None，且Swiper的displayCount属性设置为'auto'时，对应子组件在 > 视窗内不占位，但不影响导航点个数；visibility属性设置为Visibility.None或者Visibility.Hidden时，对应子组件不显示，但依然会在视窗内占位。 > > - 当Swiper子组件设置了offset属性时，会按照子组件的层级进行绘制，层级高的子组件会覆盖层级低的子组件。例如，Swiper包含3个子组件，其中第3个子组件设置了 > offset({ x : 100 })，那么在横向循环滑动中，第3个子组件会覆盖第1个子组件，此时可设置第1个子组件的zIndex属性值大于第3个子组件，使第1个子组件层级 > 高于第3个子组件。 > > - 在走焦到用户定义的子节点时，导航点、箭头会由于[焦点样式](../../../ui/arkts-common-events-focus-event.md#焦点样式)修改zIndex的行为被遮挡。 > > - 在包含大量子组件的场景中，建议采用懒加载、缓存数据、预加载数据和组件复用等方法，以优化Swiper的性能并减少内存占用。最佳实践请参考 > [优化Swiper组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-swiper_high_performance_development_guide)。 >

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
| controller | [SwiperController](arkts-arkui-swipercontroller-c.md) | 否 | 给组件绑定一个控制器，用来控制组件翻页或者预加载指定子节点。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [ArrowStyle](arkts-arkui-arrowstyle-i.md) | 左右箭头属性。 |
| [AutoPlayOptions](arkts-arkui-autoplayoptions-i.md) | 自动播放属性。 |
| [CachedCountOptions](arkts-arkui-cachedcountoptions-i.md) | 预加载子组件的配置选项。 |
| [IndicatorIconInfo](arkts-arkui-indicatoriconinfo-i.md) | 为指定的导航点索引设置的图标。 |
| [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | 导航点样式。 |
| [SwiperAnimationEvent](arkts-arkui-swiperanimationevent-i.md) | Swiper组件动画相关信息集合。 |
| [SwiperAutoFill](arkts-arkui-swiperautofill-i.md) | 自适应属性。 |
| [SwiperContentAnimatedTransition](arkts-arkui-swipercontentanimatedtransition-i.md) | Swiper自定义切换动画相关信息。 |
| [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md) | Swiper自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画视窗内的页面信息，同时，也可以通过调用该对象的finishTransition接口通知Swiper组件页面自定义动画已结束。 |
| [SwiperContentWillScrollResult](arkts-arkui-swipercontentwillscrollresult-i.md) | 滑动的相关信息，主要包括：当前页面对应的index、滑动方向上即将显示的页面index和此次滑动的位移。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md) | Swiper滑动时触发的回调，参数可参考[SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md)中的说明。 |
| [ContentWillScrollCallback](arkts-arkui-contentwillscrollcallback-t.md) | Swiper即将滑动前触发的回调，返回值表示是否允许此次滑动。 |
| [OnSwiperAnimationEndCallback](arkts-arkui-onswiperanimationendcallback-t.md) | 切换动画结束时触发的回调。 |
| [OnSwiperAnimationStartCallback](arkts-arkui-onswiperanimationstartcallback-t.md) | 切换动画开始时触发的回调。 |
| [OnSwiperGestureSwipeCallback](arkts-arkui-onswipergestureswipecallback-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [SwiperAnimationMode](arkts-arkui-swiperanimationmode-e.md) | Swiper组件翻页至指定页面的动效模式。 |
| [SwiperDisplayMode](arkts-arkui-swiperdisplaymode-e.md) | Swiper在主轴上的尺寸大小模式枚举。 |
| [SwiperNestedScrollMode](arkts-arkui-swipernestedscrollmode-e.md) | Swiper组件和父组件的嵌套滚动模式枚举。 |

