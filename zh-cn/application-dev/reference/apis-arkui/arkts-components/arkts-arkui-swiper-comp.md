# Swiper

滑块视图容器，提供子组件滑动轮播显示的能力。适用于轮播图展示、图片浏览、引导页、卡片轮播等场景。

> **说明：**

> - Swiper组件通过内置的PanGesture拖动手势实现滑动轮播效果，将[disableSwipe](arkts-arkui-swiper-comp-attribute.md#disableswipe)属性设为true > 时，会禁用该手势监听，从而阻止滑动操作。 > > - Swiper中复用NodeContainer时，禁止递归流程中子节点更新父节点状态变量。

## 子组件

可以包含子组件。

> **说明：** 
> 
> - 子组件类型：系统组件和自定义组件，支持渲染控制类型（[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)、[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)、[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md)和[Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)）。不建议子组件中混用懒加载组件（包括LazyForEach、Repeat ）和非懒加载组件，或者子组件中使用多个懒加载组件，否则可能导致懒加载组件预加载能力失效等问题。不建议在组件动画过程中对数据源进行操作，否则会导致布局出现异常。
> 
> - Swiper子组件的visibility属性设置为Visibility.None，且Swiper的displayCount属性设置为'auto'时，对应子组件在视窗内不占位，但不影响导航点个数；visibility属性设置为Visibility.None或者Visibility.Hidden时，对应子组件不显示，但依然会在视窗内占位。
> 
> - 当Swiper子组件设置了offset属性时，会按照子组件的层级进行绘制，层级高的子组件会覆盖层级低的子组件。例如，Swiper包含3个子组件，其中第3个子组件设置了offset({ x : 100 })，那么在横向循环滑动中，第3个子组件会覆盖第1个子组件，此时可设置第1个子组件的zIndex属性值大于第3个子组件，使第1个子组件层级高于第3个子组件。
> 
> - 在走焦到用户定义的子节点时，导航点、箭头会由于[焦点样式](../../../ui/arkts-common-events-focus-event.md#焦点样式)修改zIndex的行为被遮挡。
> 
> - 在包含大量子组件的场景中，建议采用懒加载、缓存数据、预加载数据和组件复用等方法，以优化Swiper的性能并减少内存占用。最佳实践请参考[优化Swiper组件加载慢丢帧问题](https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-swiper_high_performance_development_guide)。 &gt;

## Swiper

```TypeScript
Swiper(controller?: SwiperController)
```

创建滑块视图容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**卡片能力：** 从API版本10开始，该接口支持在ArkTS卡片中使用。

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

## 示例

```TypeScript
### 示例1（设置导航点交互及翻页动效）

该示例通过[changeIndex](#changeindex15)接口设置[SwiperAnimationMode](#swiperanimationmode15枚举说明)动效以跳转指定页面，并使用[onScrollStateChanged](arkts-arkui-swiper-comp-attribute.md#onscrollstatechanged)回调监听滑动状态的变化。

从API version 20开始，新增onScrollStateChanged事件。


```

```TypeScript
### 示例2（设置数字指示器）

该示例通过[DigitIndicator](arkts-arkui-digitindicator-c.md)接口，实现了数字指示器的效果和功能。


```

```TypeScript
### 示例3（设置按组翻页）

该示例通过[displayCount](arkts-arkui-swiper-comp-attribute.md#displaycount)属性实现了按组翻页效果。

从API version 24开始，新增[CachedCountOptions](#cachedcountoptions24对象说明)参数，通过该参数实现缓存的节点个数和displayCount的按组显示数量解耦。


```

```TypeScript
### 示例4（设置自定义页面切换动画）

该示例通过[customContentTransition](#customcontenttransition12)接口，实现了自定义Swiper页面按组翻页动画效果。
```

```TypeScript
// CommonUtil.ets
export class CommonUtil {
  private static isRTL: boolean = false;

  public static setIsRTL(isRTL: boolean): void {
    CommonUtil.isRTL = isRTL;
  }

  public static getIsRTL(): boolean {
    return CommonUtil.isRTL;
  }
}
```

```TypeScript

```

```TypeScript
### 示例5（设置圆点导航点超长显示）

该示例通过DotIndicator接口的[maxDisplayCount](arkts-arkui-dotindicator-c.md#maxdisplaycount)属性，实现了圆点导航点超长显示动画效果。


```

```TypeScript
### 示例6（预加载子节点）

该示例通过[preloadItems](#preloaditems18)接口实现了预加载指定子节点。
```

```TypeScript
### 示例7（实现Tabs与Swiper联动）

该示例通过[onSelected](#onselected18)接口，实现了[Tabs](ts-container-tabs.md)与Swiper联动切换。


```

```TypeScript
### 示例8（滑动行为拦截事件）

该示例通过[onContentWillScroll](arkts-arkui-swiper-comp-attribute.md#oncontentwillscroll)事件实现了单方向的滑动翻页，即只能滑动向前翻页，滑动向后翻页的行为会被拦截。


```

```TypeScript
### 示例9（演示导航点space与bottom）

该示例通过[bottom](#bottom19)和[space](#space19)接口，实现了圆点导航点与底部间距为0的间距控制以及导航点之间的间距控制。


```

```TypeScript
### 示例10（Swiper组件基于断点配置显示个数）

该示例展示了Swiper组件基于断点配置显示个数的效果。

从API version 22开始，新增[displayCount](arkts-arkui-swiper-comp-attribute.md#displaycount)接口，用于设置Swiper视窗内元素显示个数。

Swiper宽度属于[sm](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)及更小的断点区间时显示1列。



Swiper宽度属于[md](../../../ui/arkts-layout-development-grid-layout.md#栅格容器断点)断点区间时显示2列。


```

```TypeScript
### 示例11（Swiper组件模拟拖拽）

该示例展示了Swiper组件如何实现模拟拖拽。在自身不响应拖拽事件的情况下，子组件Column通过触摸事件的信息调用Swiper接口，实现类似跟手拖拽的效果。

从API version 23开始，新增[startFakeDrag](arkts-arkui-swipercontroller-c.md#startfakedrag)接口、[fakeDragBy](arkts-arkui-swipercontroller-c.md#fakedragby)接口、[stopFakeDrag](arkts-arkui-swipercontroller-c.md#stopfakedrag)接口、[isFakeDragging](arkts-arkui-swipercontroller-c.md#isfakedragging)接口，用于实现模拟拖拽。


```

```TypeScript
### 示例12（配置Swiper组件导航点图标）

该示例通过设置indicatorIcon接口，展示了Swiper组件如何配置导航点图标。

从API版本26.0.0开始，新增[indicatorIcon](arkts-arkui-dotindicator-c.md#indicatoricon)接口。
```
