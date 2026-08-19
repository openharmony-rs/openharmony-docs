# Tabs

通过页签进行内容视图切换的容器组件，每个页签对应一个内容视图。适用于应用底部导航栏、顶部页签切换、侧边栏导航等需要在不同内容视图间快速切换的场景。使用Tabs组件可以简化多视图导航的实现，提升用户切换效率。 > **说明：** > - 该组件从API version 11开始，支持安全区域避让特性，其expandSafeArea属性的默认值为expandSafeArea( > [SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])。开发者可通过重写该属性覆盖默认行为。对于API version 11之前的版本，则需配合expandSafeArea属性手动实现安全区域避 > 让。

## 子组件 仅支持子组件TabContent，以及渲染控制类型 [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)，不建议自定义组件作为子组件。并且if/else和ForEach下也仅支持 TabContent作为子组件，不建议自定义组件作为子组件。 > **说明：** > > Tabs子组件设置了通用属性visibility的值为None，或者设置值为Hidden时，对应子组件不显示，但依然会在视窗内占位。 > > 已经显示的Tabs子组件TabContent后续隐藏时不会被销毁，若需要页面懒加载和释放，可以参考 > [示例13](../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#示例13页面懒加载和释放)。 > > Tabs设置height为auto时，可根据子组件高度自适应高度大小。设置 > width为auto时，可根据子组件宽度自适应宽度大小。

## Tabs

```TypeScript
Tabs(options?: TabsOptions)
```

创建Tabs容器。

**起始版本：** 7

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsInterface-(options?: TabsOptions): TabsAttribute--><!--Device-TabsInterface-(options?: TabsOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TabsOptions | 否 | Tabs组件参数。 默认值：undefined，不设置参数时使用默认配置。 |

## 汇总

### 接口

| 名称 | 说明 |
| --- | --- |
| [BarGridColumnOptions](arkts-arkui-bargridcolumnoptions-i.md) | TabBar栅格化方式设置的对象，包括栅格模式下的column边距和间隔，以及小、中、大屏下，页签占用的columns数量。 |
| [FloatingTabBarStyle](arkts-arkui-floatingtabbarstyle-i.md) | 提供浮动条模式选项的接口。 |
| [FloatingTabBarWidth](arkts-arkui-floatingtabbarwidth-i.md) | 提供了一个接口，用于设置不同断点处的tab宽度的浮动栏宽度。 |
| [ScrollableBarModeOptions](arkts-arkui-scrollablebarmodeoptions-i.md) | Scrollable模式下的TabBar的布局样式对象。 |
| [TabContentAnimatedTransition](arkts-arkui-tabcontentanimatedtransition-i.md) | Tabs自定义切换动画相关信息。 |
| [TabContentTransitionProxy](arkts-arkui-tabcontenttransitionproxy-i.md) | Tabs自定义切换动画执行过程中，返回给开发者的proxy对象。开发者可通过该对象获取自定义动画的起始和目标页面信息，同时，也可以通过调用该对象的finishTransition接口通知Tabs组件自定义动画已结束。 |
| [TabsAnimationEvent](arkts-arkui-tabsanimationevent-i.md) | Tabs组件动画相关信息集合。 |

### 类型

| 名称 | 说明 |
| --- | --- |
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
| [AnimationMode](arkts-arkui-animationmode-e.md) | 点击TabBar页签时切换 TabContent的动画形式枚举。 |
| [BarMode](arkts-arkui-barmode-e.md) | TabBar布局模式枚举。 |
| [BarPosition](arkts-arkui-barposition-e.md) | Tabs页签位置枚举。 |
| [LayoutStyle](arkts-arkui-layoutstyle-e.md) | Scrollable模式下不滚动时的页签排布方式枚举。 |
| [TabsCacheMode](arkts-arkui-tabscachemode-e.md) | 子组件的缓存模式。 |
| [TabsNestedScrollMode](arkts-arkui-tabsnestedscrollmode-e.md) | Tabs组件和父组件的嵌套滚动模式枚举。 |

