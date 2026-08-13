# Tabs

通过页签进行内容视图切换的容器组件，每个页签对应一个内容视图。适用于应用底部导航栏、顶部页签切换、侧边栏导航等需要在不同内容视图间快速切换的场景。使用Tabs组件可以简化多视图导航的实现，提升用户切换效率。 > **说明：** > - 该组件从API version 11开始，支持安全区域避让特性，其expandSafeArea属性的默认值为expandSafeArea( > [SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])。开发者可通过重写该属性覆盖默认行为。对于API version 11之前的版本，则需配合expandSafeArea属性手动实现安全区域避 > 让。

## 子组件 仅支持子组件TabContent，以及渲染控制类型 [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md)和 [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md)，不建议自定义组件作为子组件。并且if/else和ForEach下也仅支持 TabContent作为子组件，不建议自定义组件作为子组件。 > **说明：** > > Tabs子组件设置了通用属性visibility的值为None，或者设置值为Hidden时，对应子组件不显示，但依然会在视窗内占位。 > > 已经显示的Tabs子组件TabContent后续隐藏时不会被销毁，若需要页面懒加载和释放，可以参考 > [示例13](../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#示例13页面懒加载和释放)。 > > Tabs设置height为auto时，可根据子组件高度自适应高度大小。设置 > width为auto时，可根据子组件宽度自适应宽度大小。

## Tabs

```TypeScript
Tabs(options?: TabsOptions)
```

创建Tabs容器。

**起始版本：** 7

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为7。

**废弃版本：** -1

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-TabsInterface-(options?: TabsOptions): TabsAttribute--><!--Device-TabsInterface-(options?: TabsOptions): TabsAttribute-End-->

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TabsOptions | 否 | Tabs组件参数。 默认值：undefined，不设置参数时使用默认配置。 |

## 汇总

- [BarGridColumnOptions](arkts-arkui-bargridcolumnoptions-i.md)
- [FloatingTabBarStyle](arkts-arkui-floatingtabbarstyle-i.md)
- [FloatingTabBarWidth](arkts-arkui-floatingtabbarwidth-i.md)
- [ScrollableBarModeOptions](arkts-arkui-scrollablebarmodeoptions-i.md)
- [TabContentAnimatedTransition](arkts-arkui-tabcontentanimatedtransition-i.md)
- [TabContentTransitionProxy](arkts-arkui-tabcontenttransitionproxy-i.md)
- [TabsAnimationEvent](arkts-arkui-tabsanimationevent-i.md)
- [OnTabsAnimationEndCallback](arkts-arkui-ontabsanimationendcallback-t.md)
- [OnTabsAnimationStartCallback](arkts-arkui-ontabsanimationstartcallback-t.md)
- [OnTabsContentDidScrollCallback](arkts-arkui-ontabscontentdidscrollcallback-t.md)
- [OnTabsContentWillChangeCallback](arkts-arkui-ontabscontentwillchangecallback-t.md)
- [OnTabsGestureSwipeCallback](arkts-arkui-ontabsgestureswipecallback-t.md)
- [TabsCustomContentTransitionCallback](arkts-arkui-tabscustomcontenttransitioncallback-t.md)
- [UIMaterial](arkts-arkui-uimaterial-t.md)
- [AnimationMode](arkts-arkui-animationmode-e.md)
- [BarMode](arkts-arkui-barmode-e.md)
- [BarPosition](arkts-arkui-barposition-e.md)
- [LayoutStyle](arkts-arkui-layoutstyle-e.md)
- [TabsCacheMode](arkts-arkui-tabscachemode-e.md)
- [TabsNestedScrollMode](arkts-arkui-tabsnestedscrollmode-e.md)
