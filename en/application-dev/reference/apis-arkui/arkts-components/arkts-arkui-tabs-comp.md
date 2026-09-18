# Tabs

The **Tabs** component is a container component that allows users to switch between content views through tabs. Each tab page corresponds to a content view.

> **NOTE** > > - > > - Since API version 11, this component supports the safe area avoidance feature. The default value of the > [expandSafeArea]{} > **expandSafeArea([SafeAreaType.SYSTEM], [SafeAreaEdge.BOTTOM])**. You can override the default behavior by > rewriting this attribute. For versions earlier than API version 11, you need to manually implement safe area > avoidance together with the **expandSafeArea** attribute.

## Child Components

Only the child component TabContent and rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) and [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md) are supported. You are advised not to use custom components as child components. If **if/else** or **ForEach** is used, only **TabContent** can be used as the child component. You are advised not to use custom components as child components.

> **NOTE:** 
> 
> If the child component has the **visibility** attribute set to **None** or **Hidden**, it is hidden but still takes
> up space in the layout.
> 
> When a displayed **Tabs** child component **TabContent** is hidden, it is not destroyed. For details about how to
> implement lazy loading and release on the page, see
> [Example 13](../../../reference/apis-arkui/arkui-ts/ts-container-tabs.md#example-13-implementing-lazy-loading-and-resource-release-of-pages).
> 
> 
> If height is set to **auto** for **Tabs**, the tab height can be
> automatically adjusted based on that of the child component. When width
> is set to **auto**, the tab width can be automatically adjusted based on that of the child component.

## Tabs

```TypeScript
Tabs(options?: TabsOptions)
```

Create a **Tabs** container.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TabsOptions](arkts-arkui-tabsoptions-i.md) | No | Options of the **Tabs** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BarGridColumnOptions](arkts-arkui-bargridcolumnoptions-i.md) | Implements a **BarGridColumnOptions** object for setting the visible area of the tab bar in grid mode, including the column margin and gutter, as well as the number of columns occupied by tabs under small, medium, and large screen sizes. |
| [DividerStyle](arkts-arkui-dividerstyle-i.md) | Describes the divider style. |
| [FloatingTabBarStyle](arkts-arkui-floatingtabbarstyle-i.md) | Provides an interface for the options for the floating bar mode. |
| [FloatingTabBarWidth](arkts-arkui-floatingtabbarwidth-i.md) | Provides an interface for the options for the floating bar width of the tab width at different breakpoints. |
| [ScrollableBarModeOptions](arkts-arkui-scrollablebarmodeoptions-i.md) | Implements a **ScrollableBarModeOptions** object. |
| [TabContentAnimatedTransition](arkts-arkui-tabcontentanimatedtransition-i.md) | Provides the information about the custom tab switching animation. |
| [TabContentTransitionProxy](arkts-arkui-tabcontenttransitionproxy-i.md) | Implements the proxy object returned during the execution of the custom switching animation of the **Tabs** component. You can use this object to obtain the start and target pages for the custom tab switching animation. In addition, you can call the **finishTransition** API of this object to notify the **Tabs** component of the ending of the custom animation. |
| [TabsAnimationEvent](arkts-arkui-tabsanimationevent-i.md) | Describes the animation information of the **Tabs** component. |
| [TabsBreakpointType](arkts-arkui-tabsbreakpointtype-i.md) | Defines the value type for different Tabs container sizes. |
| [TabsOptions](arkts-arkui-tabsoptions-i.md) | Provides parameters for configuring the **Tabs** component, including tab positions, the current index of the displayed tab, the **Tabs** controller, and universal attributes for the **TabBar**. |
| [TabsSidebarSearchableOptions](arkts-arkui-tabssidebarsearchableoptions-i.md) | Defines the options for the searchable sidebar tab bar. |

### Types

| Name | Description |
| --- | --- |
| [CommonModifier](arkts-arkui-commonmodifier-t.md) | Defines a parameter object for the **Tabs** component. |
| [OnTabsAnimationEndCallback](arkts-arkui-ontabsanimationendcallback-t.md) | Defines the callback triggered when the tab switching animation ends. |
| [OnTabsAnimationStartCallback](arkts-arkui-ontabsanimationstartcallback-t.md) | Defines the callback triggered when the tab switching animation starts. |
| [OnTabsContentDidScrollCallback](arkts-arkui-ontabscontentdidscrollcallback-t.md) | Defines the callback triggered when content in the **Tabs** component scrolls. |
| [OnTabsContentWillChangeCallback](arkts-arkui-ontabscontentwillchangecallback-t.md) | Defines the callback invoked when a new page is about to be displayed. |
| [OnTabsGestureSwipeCallback](arkts-arkui-ontabsgestureswipecallback-t.md) | Defines the callback triggered on a frame-by-frame basis during a swipe-based page turn. |
| [TabsCustomContentTransitionCallback](arkts-arkui-tabscustomcontenttransitioncallback-t.md) | Defines the callback invoked when the custom tab transition animation starts. |
| [TabsSidebarSearchFilterCallback](arkts-arkui-tabssidebarsearchfiltercallback-t.md) | Search filter callback. |
| [UIMaterial](arkts-arkui-uimaterial-t.md) | [UIMaterial](arkts-arkui-uimaterial-t.md) |

### Enums

| Name | Description |
| --- | --- |
| [AnimationMode](arkts-arkui-animationmode-e.md) | Enumerates the animation modes for switching between tabs. |
| [BarMode](arkts-arkui-barmode-e.md) | Enumerates layout modes of the tab bar. |
| [BarPosition](arkts-arkui-barposition-e.md) | Enumerates the positions of the **Tabs** component. |
| [LayoutStyle](arkts-arkui-layoutstyle-e.md) | Enumerates the tab layout styles of the tab bar when not scrolling in scrollable mode. |
| [TabBarDisplayMode](arkts-arkui-tabbardisplaymode-e.md) | Enumerates the actual display modes of the tab bar under different Tabs container sizes. This enum is used in [barDisplayModeBreakpoint](arkts-arkui-tabs-comp-attribute.md#bardisplaymodebreakpoint) to specify the display mode for different breakpoint sizes. It is only meaningful when **TabBarStyle** is set to **SIDEBAR_ADAPTABLE** or **SIDEBAR**. |
| [TabBarStyle](arkts-arkui-tabbarstyle-e.md) | Enumerates the display styles of the tab bar. |
| [TabsCacheMode](arkts-arkui-tabscachemode-e.md) | Enumerates the caching modes for child components. |
| [TabsNestedScrollMode](arkts-arkui-tabsnestedscrollmode-e.md) | Enumerates the nested scrolling modes of the **Tabs** component and its parent container. |

## Examples

```TypeScript
### Example 1: Setting the Layout Mode of Tab Bar

This example uses [barMode](#barmode) to implement the evenly distributed layout of tabs and the layout by actual length, and demonstrates the scrollable effect when the total length of the tab layout exceeds the total length of the tab bar.


```

```TypeScript
### Example 2: Setting the Layout Style for a Scrollable TabBar

This example implements the ScrollableBarModeOptions parameter of [barMode](#barmode10-1), which is valid only in Scrollable mode.


```

```TypeScript
### Example 3: Implementing Custom Tab Switching Synchronization

This example uses [onAnimationStart](#onanimationstart11) and [onChange](#onchange) to implement the linkage between the custom tab bar and tab content during switching.


```

```TypeScript
### Example 4: Setting the Basic Attributes of the Divider

This example uses [divider](#divider10) to demonstrate various attributes of the divider.


```

```TypeScript
### Example 5: Setting Tab Bar Fading

This example uses [fadingEdge](#fadingedge10) to implement fading and non-fading when switching child tabs.


```

```TypeScript
### Example 6: Implementing TabBar Overlay on TabContent

This example uses [barOverlap](#baroverlap10) to set whether the tab bar is blurred behind and overlays the TabContent.


```

```TypeScript
### Example 7: Setting the Visible Area for the Tab Bar in Responsive Grid Mode

This example uses [barGridAlign](arkts-arkui-tabs-comp-attribute.md#bargridalign) to set the visible area of the tab bar in a grid-based manner.


```

```TypeScript
### Example 8: Implementing a Custom Tab Switching Animation

In this example, the [customContentTransition](#customcontenttransition11) API is used to define a custom switching animation for the Tabs page.


```

```TypeScript
### Example 9: Implementing Tab Switching Interception

This example implements custom interception of page switching via gesture swiping through [onContentWillChange](#oncontentwillchange12).


```

```TypeScript
### Example 10: Customizing the Tab Bar Switching Animation

This example implements the switching animation of a custom tab bar through APIs such as [onChange](#onchange), [onAnimationStart](#onanimationstart11), [onAnimationEnd](#onanimationend11), and [onGestureSwipe](#ongestureswipe11).
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
### Example 11: Preloading Child Nodes

This example demonstrates how to use the [preloadItems](#preloaditems12) API to preload specified child nodes.
```

```TypeScript
### Example 12: Setting Tab Bar Translation and Opacity

This example sets the translation distance and opacity of the tab bar through APIs such as [setTabBarTranslate](arkts-arkui-tabscontroller-c.md#settabbartranslate) and [setTabBarOpacity](arkts-arkui-tabscontroller-c.md#settabbaropacity).


```

```TypeScript
### Example 13: Implementing Lazy Loading and Resource Release of Pages

This example uses a custom [TabBar](ts-container-tabcontent.md#tabbar) and [Swiper](ts-container-swiper.md) together with [LazyForEach](ts-rendering-control-lazyforeach.md) to implement page lazy loading and release.


```

```TypeScript
### Example 14: Implementing the Tab Switching Animation

This example sets the [animationMode](#animationmode12) attribute to implement the page-turning animation.


```

```TypeScript
### Example 15: Enabling Tabs to Exceed the Tab Bar Area

This example uses the barModifier in [TabsOptions](arkts-arkui-tabsoptions-i.md) to set the clip attribute of the TabBar to display tabs beyond the tab bar area.

Since API version 15, the barModifier API has been added to TabsOptions.


```

```TypeScript
### Example 16: Aligning Tabs

This example uses the barModifier in [TabsOptions](arkts-arkui-tabsoptions-i.md) to set the align attribute of the TabBar to implement the tab alignment layout effect.

Since API version 15, the barModifier API is added to TabsOptions.


```

```TypeScript
### Example 17: Synchronizing Tabs and TabBar Synchronously

This example uses the [onSelected](#onselected18) API to implement synchronized switching between Tabs and TabBar.

Since API version 18, the onSelected API is added.


```

```TypeScript
### Example 18: Releasing the Tabs Child Components

This example releases the child components of Tabs by setting the [cachedMaxCount](arkts-arkui-tabs-comp-attribute.md#cachedmaxcount) attribute.

Since API version 19, the cachedMaxCount API is added.
```

```TypeScript
### Example 19: Setting the Tab Bar Background Blur Effect

This example sets the background blur style and effect of the tab bar through [barBackgroundBlurStyle](arkts-arkui-tabs-comp-attribute.md#barbackgroundblurstyle) and [barBackgroundEffect](arkts-arkui-tabs-comp-attribute.md#barbackgroundeffect), respectively.

Since API version 18, the barBackgroundBlurStyle and barBackgroundEffect APIs are added.


```

```TypeScript
### Example 20: Setting the Edge Sliding Effect

This example uses [edgeEffect](#edgeeffect12) to implement different edge rebound effects.


```

```TypeScript
### Example 21: Setting the Tab Switching Animation Curve

This example shows how to set the page switching animation curve of Tabs through the [animationCurve](arkts-arkui-tabs-comp-attribute.md#animationcurve) API, and set the duration of the page switching animation in combination with animationDuration.

Since API version 20, the animationCurve API is added.


```

```TypeScript
### Example 22: Listening for Swipe Events on the Tabs Page

This example shows how to set a callback for Tabs swiping through the [onContentDidScroll](#oncontentdidscroll23) API.

Since API version 23, the onContentDidScroll API is added.
```

```TypeScript
### Example 23: Implementing Nested Scrolling of Tabs

This example shows how to set the nested scrolling effect of Tabs through the [nestedScroll](#nestedscroll24) API.

Since API version 24, the nestedScroll API is added.
```

```TypeScript
### Example 24 Setting the TabBar Floating Style

This example shows how to set the floating style and immersive material of the back panel for the tab bar through the [barFloatingStyle](arkts-arkui-tabs-comp-attribute.md#barfloatingstyle) API.

Since API version 26.0.0, the barFloatingStyle API is added.
```
