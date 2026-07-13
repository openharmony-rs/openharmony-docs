# Tabs

通过页签进行内容视图切换的容器组件，每个页签对应一个内容视图。

> **说明：**

> - 该组件从API version 11开始，支持安全区域避让特性，其[expandSafeArea]{@link CommonMethod#expandSafeArea}属性的默认值为expandSafeArea(
> [SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])。开发者可通过重写该属性覆盖默认行为。对于API version 11之前的版本，则需配合expandSafeArea属性手动实现安全区域避
> 让。


## Tabs

```TypeScript
Tabs(options?: TabsOptions)
```

创建Tabs容器。

**起始版本：** 7

**元服务API：** 从API版本11开始，该接口支持在元服务API中使用。

**系统能力：** SystemCapability.ArkUI.ArkUI.Full

**参数:**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| options | TabsOptions | 否 | Tabs组件参数。 |

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
