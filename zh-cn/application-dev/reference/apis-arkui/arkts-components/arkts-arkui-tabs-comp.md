# Tabs

通过页签进行内容视图切换的容器组件，每个页签对应一个内容视图。适用于应用底部导航栏、顶部页签切换、侧边栏导航等需要在不同内容视图间快速切换的场景。使用Tabs组件可以简化多视图导航的实现，提升用户切换效率。

> **说明：**

> - 该组件从API version 11开始，支持安全区域避让特性，其[expandSafeArea](arkts-arkui-commonmethod-c.md#expandsafearea)属性的默认值为expandSafeArea( > [SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])。开发者可通过重写该属性覆盖默认行为。对于API version 11之前的版本，则需配合expandSafeArea属性手动实现安全区域避 > 让。

## 子组件

仅支持子组件TabContent，以及渲染控制类型[if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)，不建议自定义组件作为子组件。并且if/else和ForEach下也仅支持TabContent作为子组件，不建议自定义组件作为子组件。

> **说明：** 
> 
> Tabs子组件设置了通用属性visibility的值为None，或者设置值为Hidden时，对应子组件不显示，但依然会在视窗内占位。
> 
> 已经显示的Tabs子组件TabContent后续隐藏时不会被销毁，若需要页面懒加载和释放，可以参考
> 示例13。
> 
> Tabs设置height为auto时，可根据子组件高度自适应高度大小。设置
> width为auto时，可根据子组件宽度自适应宽度大小。

## Tabs

```TypeScript
Tabs(options?: TabsOptions)
```

创建Tabs容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | [TabsOptions](arkts-arkui-tabsoptions-i.md) | 否 | Tabs组件参数。 默认值：undefined，不设置参数时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BarGridColumnOptions](arkts-arkui-bargridcolumnoptions-i.md) | TabBar栅格化方式设置的对象，包括栅格模式下的column边距和间隔，以及小、中、大屏下，页签占用的columns数量。 |
| [DividerStyle](arkts-arkui-dividerstyle-i.md) | 分割线样式对象。 |
| [FloatingTabBarStyle](arkts-arkui-floatingtabbarstyle-i.md) | 提供浮动条模式选项的接口。 |
| [FloatingTabBarWidth](arkts-arkui-floatingtabbarwidth-i.md) | 提供了一个接口，用于设置不同断点处的tab宽度的浮动栏宽度。 |
| [ScrollableBarModeOptions](arkts-arkui-scrollablebarmodeoptions-i.md) | Scrollable模式下的TabBar的布局样式对象。 |
| [TabContentAnimatedTransition](arkts-arkui-tabcontentanimatedtransition-i.md) | Tabs自定义切换动画相关信息。 |
| [TabContentTransitionProxy](arkts-arkui-tabcontenttransitionproxy-i.md) | Tabs自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画的起始和目标页面信息，同时，也可以通过调用该对象的finishTransition接口通知Tabs组件自定义动画已结束。 |
| [TabsAnimationEvent](arkts-arkui-tabsanimationevent-i.md) | Tabs组件动画相关信息集合。 |
| [TabsOptions](arkts-arkui-tabsoptions-i.md) | Tabs组件参数，设置Tabs的页签位置，当前显示页签的索引，Tabs控制器和页签栏（TabBar）的通用属性。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [CommonModifier](arkts-arkui-commonmodifier-t.md) | CommonModifier类型用于设置Tabs组件参数。 |
| [OnTabsAnimationEndCallback](arkts-arkui-ontabsanimationendcallback-t.md) | 切换动画结束时触发的回调。 |
| [OnTabsAnimationStartCallback](arkts-arkui-ontabsanimationstartcallback-t.md) | 切换动画开始时触发的回调。 |
| [OnTabsContentDidScrollCallback](arkts-arkui-ontabscontentdidscrollcallback-t.md) | Tabs滑动时触发的回调。 |
| [OnTabsContentWillChangeCallback](arkts-arkui-ontabscontentwillchangecallback-t.md) | 自定义Tabs页面切换拦截事件能力，新页面即将显示时触发的回调。 |
| [OnTabsGestureSwipeCallback](arkts-arkui-ontabsgestureswipecallback-t.md) | 在页面跟手滑动过程中，逐帧触发的回调。 |
| [TabsCustomContentTransitionCallback](arkts-arkui-tabscustomcontenttransitioncallback-t.md) | 自定义Tabs页面切换动画开始时触发的回调。 |
| [UIMaterial](arkts-arkui-uimaterial-t.md) | 材质 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AnimationMode](arkts-arkui-animationmode-e.md) | 点击[TabBar](arkts-arkui-tabcontent-comp-attribute.md#tabbar)页签时切换TabContent的动画形式枚举。 |
| [BarMode](arkts-arkui-barmode-e.md) | TabBar布局模式枚举。 |
| [BarPosition](arkts-arkui-barposition-e.md) | Tabs页签位置枚举。 |
| [LayoutStyle](arkts-arkui-layoutstyle-e.md) | [Scrollable](arkts-arkui-tabs-comp-attribute.md#barmode)模式下不滚动时的页签排布方式枚举。 |
| [TabsCacheMode](arkts-arkui-tabscachemode-e.md) | 子组件的缓存模式。 |
| [TabsNestedScrollMode](arkts-arkui-tabsnestedscrollmode-e.md) | Tabs组件和父组件的嵌套滚动模式枚举。 |

## 示例

```TypeScript
### 示例1（设置TabBar的布局模式）

本示例通过[barMode](#barmode)分别实现了页签均分布局和以实际长度布局，且展示了当页签布局长度之和超过了TabBar总长度后可滑动的效果。


```

```TypeScript
### 示例2（设置Scrollable模式下的TabBar的布局样式）

本示例实现了[barMode](#barmode10-1)的ScrollableBarModeOptions参数，该参数仅在Scrollable模式下有效。


```

```TypeScript
### 示例3（自定义页签切换联动）

本示例通过[onAnimationStart](#onanimationstart11)、[onChange](#onchange)实现切换时自定义tabBar和TabContent的联动。


```

```TypeScript
### 示例4（分割线基本属性）

本示例通过[divider](#divider10)实现了分割线各种属性的展示。


```

```TypeScript
### 示例5（设置TabBar渐隐）

本示例通过[fadingEdge](#fadingedge10)实现了切换子页签渐隐和不渐隐。


```

```TypeScript
### 示例6（设置TabBar叠加在TabContent内容上）

本示例通过[barOverlap](#baroverlap10)实现了TabBar是否背后变模糊并叠加在TabContent之上。


```

```TypeScript
### 示例7（设置TabBar栅格化可见区域）

本示例通过[barGridAlign](arkts-arkui-tabs-comp-attribute.md#bargridalign)实现了以栅格化方式设置TabBar的可见区域。


```

```TypeScript
### 示例8（自定义Tabs页面切换动画）

本示例通过[customContentTransition](#customcontenttransition11)实现了自定义Tabs页面的切换动画。


```

```TypeScript
### 示例9（页面切换拦截）

本示例通过[onContentWillChange](#oncontentwillchange12)实现了自定义页面手势滑动切换拦截。


```

```TypeScript
### 示例10（自定义TabBar切换动画）

本示例通过[onChange](#onchange)、[onAnimationStart](#onanimationstart11)、[onAnimationEnd](#onanimationend11)、[onGestureSwipe](#ongestureswipe11)等接口实现了自定义TabBar的切换动画。
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
### 示例11（预加载子节点）

本示例通过[preloadItems](#preloaditems12)接口实现了预加载指定子节点。
```

```TypeScript
### 示例12（设置TabBar平移距离和不透明度）

本示例通过[setTabBarTranslate](arkts-arkui-tabscontroller-c.md#settabbartranslate)、[setTabBarOpacity](arkts-arkui-tabscontroller-c.md#settabbaropacity)等接口设置了TabBar的平移距离和不透明度。


```

```TypeScript
### 示例13（页面懒加载和释放）

本示例通过使用自定义[TabBar](ts-container-tabcontent.md#tabbar)与[Swiper](ts-container-swiper.md)配合[LazyForEach](ts-rendering-control-lazyforeach.md)实现页面懒加载和释放。


```

```TypeScript
### 示例14（设置翻页动效）

本示例通过设置[animationMode](#animationmode12)属性，实现了翻页的动效。


```

```TypeScript
### 示例15（页签超出TabBar区域显示）

该示例通过使用[TabsOptions](arkts-arkui-tabsoptions-i.md)中的barModifier设置tabBar的clip属性实现页签超出tabBar区域显示效果。

从API version 15开始，在TabsOptions中新增了barModifier接口。


```

```TypeScript
### 示例16（页签对齐布局）

本示例通过使用[TabsOptions](arkts-arkui-tabsoptions-i.md)中的barModifier设置tabBar的align属性实现页签对齐布局效果。

从API version 15开始，在TabsOptions中新增了barModifier接口。


```

```TypeScript
### 示例17（Tabs与TabBar同步切换）

该示例通过[onSelected](#onselected18)接口，实现了Tabs与TabBar的同步切换。

从API version 18开始，新增了onSelected接口。


```

```TypeScript
### 示例18（释放Tabs子组件）

该示例通过设置[cachedMaxCount](arkts-arkui-tabs-comp-attribute.md#cachedmaxcount)属性，实现了Tabs子组件的释放。

从API version 19开始，新增了cachedMaxCount接口。
```

```TypeScript
### 示例19（设置TabBar背景模糊效果）

该示例分别通过[barBackgroundBlurStyle](arkts-arkui-tabs-comp-attribute.md#barbackgroundblurstyle)和[barBackgroundEffect](arkts-arkui-tabs-comp-attribute.md#barbackgroundeffect)设置TabBar页签栏的背景模糊样式和效果。

从API version 18开始，新增了barBackgroundBlurStyle和barBackgroundEffect接口。


```

```TypeScript
### 示例20（设置边缘滑动效果）

该示例通过[edgeEffect](#edgeeffect12)实现了不同的边缘回弹效果。


```

```TypeScript
### 示例21（Tabs设置翻页动画曲线）

该示例展示了如何通过[animationCurve](arkts-arkui-tabs-comp-attribute.md#animationcurve)接口设置Tabs翻页动画曲线，并结合animationDuration设置翻页动画的时长。

从API version 20开始，新增了animationCurve接口。


```

```TypeScript
### 示例22（监听Tabs页面滑动事件）

该示例展示了如何通过[onContentDidScroll](#oncontentdidscroll23)接口设置Tabs滑动时的回调。

从API version 23开始，新增onContentDidScroll接口。


```

```TypeScript
### 示例23（Tabs嵌套滚动）

该示例展示了如何通过[nestedScroll](#nestedscroll24)接口设置Tabs嵌套滚动效果。

从API version 24开始，新增nestedScroll接口。


```

```TypeScript
### 示例24（TabBar悬浮样式）

本示例展示了如何通过[barFloatingStyle](arkts-arkui-tabs-comp-attribute.md#barfloatingstyle)接口设置TabBar的悬浮样式和背板沉浸式材质。

该示例配图为高算力设备强档效果，组件沉浸光感效果会根据设备算力与用户在系统中设置的沉浸光感效果自适应调整，开发者无需额外适配。

从API版本26.0.0开始，新增barFloatingStyle接口。
```
