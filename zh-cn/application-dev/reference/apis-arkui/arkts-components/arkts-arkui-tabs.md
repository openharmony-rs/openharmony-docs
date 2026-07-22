# Tabs

通过页签进行内容视图切换的容器组件，每个页签对应一个内容视图。

> **说明：**

> - 该组件从API version 11开始，支持安全区域避让特性，其[expandSafeArea]{@link CommonMethod#expandSafeArea}属性的默认值为expandSafeArea(
> [SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])。开发者可通过重写该属性覆盖默认行为。对于API version 11之前的版本，则需配合expandSafeArea属性手动实现安全区域避
> 让。

## 子组件

仅支持子组件[TabContent]{@link tab_content}，以及渲染控制类型[if/else](docroot://ui/rendering-control/arkts-rendering-control-ifelse.md)和[ForEach](docroot://ui/rendering-control/arkts-rendering-control-foreach.md)，不建议自定义组件作为子组件。并且if/else和ForEach下也仅支持TabContent作为子组件，不建议自定义组件作为子组件。
> **说明：**  
>  
> Tabs子组件设置了通用属性[visibility]{@link CommonMethod#visibility}的值为None，或者设置值为Hidden时，对应子组件不显示，但依然会在视窗内占位。  
>  
> 已经显示的Tabs子组件TabContent后续隐藏时不会被销毁，若需要页面懒加载和释放，可以参考  
> [示例13](docroot://reference/apis-arkui/arkui-ts/ts-container-tabs.md#示例13页面懒加载和释放)。  
>  
> Tabs设置[height]{@link CommonMethod#height(value: Length)}为auto时，可根据子组件高度自适应高度大小。设置  
> [width]{@link CommonMethod#width(value: Length)}为auto时，可根据子组件宽度自适应宽度大小。

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
| options | [TabsOptions](arkts-arkui-tabsoptions-i.md) | 否 | Tabs组件参数。 |

## 汇总

- [BarGridColumnOptions](arkts-arkui-tabs-bargridcolumnoptions-i.md)
- [DividerStyle](arkts-arkui-tabs-dividerstyle-i.md)
- [FloatingTabBarStyle](arkts-arkui-tabs-floatingtabbarstyle-i.md)
- [FloatingTabBarWidth](arkts-arkui-tabs-floatingtabbarwidth-i.md)
- [ScrollableBarModeOptions](arkts-arkui-tabs-scrollablebarmodeoptions-i.md)
- [TabContentAnimatedTransition](arkts-arkui-tabs-tabcontentanimatedtransition-i.md)
- [TabContentTransitionProxy](arkts-arkui-tabs-tabcontenttransitionproxy-i.md)
- [TabsAnimationEvent](arkts-arkui-tabs-tabsanimationevent-i.md)
- [TabsOptions](arkts-arkui-tabs-tabsoptions-i.md)
- [CommonModifier](arkts-arkui-tabs-commonmodifier-t.md)
- [OnTabsAnimationEndCallback](arkts-arkui-tabs-ontabsanimationendcallback-t.md)
- [OnTabsAnimationStartCallback](arkts-arkui-tabs-ontabsanimationstartcallback-t.md)
- [OnTabsContentDidScrollCallback](arkts-arkui-tabs-ontabscontentdidscrollcallback-t.md)
- [OnTabsContentWillChangeCallback](arkts-arkui-tabs-ontabscontentwillchangecallback-t.md)
- [OnTabsGestureSwipeCallback](arkts-arkui-tabs-ontabsgestureswipecallback-t.md)
- [TabsCustomContentTransitionCallback](arkts-arkui-tabs-tabscustomcontenttransitioncallback-t.md)
- [UIMaterial](arkts-arkui-tabs-uimaterial-t.md)
- [AnimationMode](arkts-arkui-tabs-animationmode-e.md)
- [BarMode](arkts-arkui-tabs-barmode-e.md)
- [BarPosition](arkts-arkui-tabs-barposition-e.md)
- [LayoutStyle](arkts-arkui-tabs-layoutstyle-e.md)
- [TabsCacheMode](arkts-arkui-tabs-tabscachemode-e.md)
- [TabsNestedScrollMode](arkts-arkui-tabs-tabsnestedscrollmode-e.md)
