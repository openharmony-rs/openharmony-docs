# Swiper

The **Swiper** component is able to display child components in a carousel-like manner.

> **NOTE**

> - The **Swiper** component implements the scrolling carousel effect through the built-in > PanGesture gesture. When the [disableSwipe](arkts-arkui-swiper-comp-attribute.md#disableswipe) attribute is set > to **true**, the gesture listening is disabled, thereby preventing the scrolling operation. > > - When NodeContainer is reused in the **Swiper** component, recursive updates of parent > component state variables by child nodes are prohibited.

## Child Components

Supported

> **NOTE:** 
> 
> - Allowed child component types: built-in and custom components, including rendering control types ([if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md),[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md)). To maximize the benefits of lazy loading, avoid mixing lazy loading components (including **LazyForEach** and **Repeat**) and non-lazy loading components, and exercise caution when using multiple lazy loading components. Avoid modifying the data source while an animation is in progress, as doing so can lead to layout issues.
> 
> - If a child component has its [visibility](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-visibility.md#visibility) attribute set to **Visibility.None** and the **Swiper** component has its **displayCount** attribute set to **'auto'**, the child component does not take up space in the viewport, but does not affect the number of navigation points. If a child component has its **visibility** attribute set to **Visibility.None** or **Visibility.Hidden**, it takes up space in the viewport, but is not displayed.
> 
> - Child components of the **Swiper** component are drawn based on their level if they have the offset attribute set. A child component with a higher level overwrites one with a lower level. For example, if the **Swiper** contains three child components and **offset({ x: 100 })** is set for the third child component, the third child component overwrites the first child component during horizontal loop playback. To prevent the first child component from being overwritten, set its zIndexattribute to a value greater than that of the third child component.
> 
> - When focus is moved to a custom child node, navigation indicators and arrows may be obscured by [focus styles](../../../ui/arkts-common-events-focus-event.md#focus-style) modifications that change **zIndex**.
> 
> - For a **Swiper** component with many child components, you can optimize the performance and reduce memory consumption by using lazy loading, data caching, preloading, and component reuse techniques. For best practices,see [Optimizing Frame Loss During Swiper Component Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-swiper_high_performance_development_guide). &gt;

## Swiper

```TypeScript
Swiper(controller?: SwiperController)
```

Creates a **Swiper** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| controller | [SwiperController](arkts-arkui-swipercontroller-c.md) | No | Controller to bind to the component to manage page switching and preload specific child components. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ArrowStyle](arkts-arkui-arrowstyle-i.md) | Describes the left and right arrow attributes. |
| [AutoPlayOptions](arkts-arkui-autoplayoptions-i.md) | Defines the properties for controlling the automatic playback behavior. |
| [CachedCountOptions](arkts-arkui-cachedcountoptions-i.md) | Describes the configuration options for child components to be preloaded. |
| [IndicatorIconInfo](arkts-arkui-indicatoriconinfo-i.md) | Set the indicator item's icon for a specified index. |
| [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | Defines the style of the navigation indicator. |
| [SwiperAnimationEvent](arkts-arkui-swiperanimationevent-i.md) | Describes the animation information of the **Swiper** component. |
| [SwiperAutoFill](arkts-arkui-swiperautofill-i.md) | Describes the auto-fill attribute. |
| [SwiperContentAnimatedTransition](arkts-arkui-swipercontentanimatedtransition-i.md) | Provides the information about the custom page transition animation. |
| [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md) | Implements the proxy object returned during the execution of the custom page transition animation of the **Swiper** component. You can use this object to obtain the page information in the custom animation viewport. You can also call the **finishTransition** API of this object to notify the **Swiper** component that the custom animation has finished playing. |
| [SwiperContentWillScrollResult](arkts-arkui-swipercontentwillscrollresult-i.md) | Provides information related to the upcoming scroll action, including the index of the current page, the index of the page that will be displayed in the scroll direction, and the displacement of the scroll action. |

### Types

| Name | Description |
| --- | --- |
| [ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md) | Triggered during the swipe action of the **Swiper** component. For details about the parameters, see [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md). |
| [ContentWillScrollCallback](arkts-arkui-contentwillscrollcallback-t.md) | Defines the callback triggered when the **Swiper** component is about to scroll. The return value indicates whether the scroll action is allowed. |
| [OnSwiperAnimationEndCallback](arkts-arkui-onswiperanimationendcallback-t.md) | Defines the callback triggered when the page transition animation ends. |
| [OnSwiperAnimationStartCallback](arkts-arkui-onswiperanimationstartcallback-t.md) | Defines the callback triggered when the page transition animation starts. |
| [OnSwiperGestureSwipeCallback](arkts-arkui-onswipergestureswipecallback-t.md) | Defines the callback triggered on a frame-by-frame basis when the page is turned by a swipe. |

### Enums

| Name | Description |
| --- | --- |
| [SwiperAnimationMode](arkts-arkui-swiperanimationmode-e.md) | Enumerates the animation mode for moving to a specific page in the **Swiper** component. |
| [SwiperDisplayMode](arkts-arkui-swiperdisplaymode-e.md) | Enumerates the modes in which elements are displayed along the main axis. |
| [SwiperNestedScrollMode](arkts-arkui-swipernestedscrollmode-e.md) | Enumerates the nested scrolling modes of the **Swiper** component and its parent container. |

## Examples

```TypeScript
### Example 1: Setting the Navigation Indicator Interaction and Page Turning Effect

In this example, the [changeIndex](#changeindex15) API is used to set the [SwiperAnimationMode](arkts-arkui-swiperanimationmode-e.md) animation effect to jump to a specified page, and the [onScrollStateChanged](arkts-arkui-swiper-comp-attribute.md#onscrollstatechanged) callback is used to listen for the scrolling state changes.

The onScrollStateChanged event is supported since API version 20.


```

```TypeScript
### Example 2: Implementing a Digit Indicator

This example uses the [DigitIndicator](arkts-arkui-digitindicator-c.md) API to implement a digit-style indicator.


```

```TypeScript
### Example 3: Setting the Page Turning by Group

This example demonstrates how to implement the group-based page turning effect using the [displayCount](arkts-arkui-swiper-comp-attribute.md#displaycount) attribute.

Since API version 24, the [CachedCountOptions](arkts-arkui-cachedcountoptions-i.md) parameter is added to decouple the number of cached nodes from the number of nodes displayed by group in the displayCount attribute.


```

```TypeScript
### Example 4: Customizing the Page Transition Animation

This example presents how to implement a custom page transition animation for the Swiper component through the [customContentTransition](#customcontenttransition12) API.
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
### Example 5: Configuring Overflow for the Dot-Style Indicator

This example demonstrates how to implement an animation for the overflow effect when the number of navigation dots exceeds the limit set through the [maxDisplayCount](arkts-arkui-dotindicator-c.md#maxdisplaycount) property of the DotIndicator API.


```

```TypeScript
### Example 6: Preloading Child Nodes

This example demonstrates how to use the [preloadItems](#preloaditems18) API to preload specified child nodes.
```

```TypeScript
### Example 7: Implementing Synchronized Switching Between the Tabs and Swiper Components

This example associates [Tabs](ts-container-tabs.md) with the Swiper component through the [onSelected](#onselected18) API.


```

```TypeScript
### Example 8: Intercepting the Scrolling Behavior

This example demonstrates how to use the [onContentWillScroll](arkts-arkui-swiper-comp-attribute.md#oncontentwillscroll) event to allow only forward scrolling and intercept backward scrolling.


```

```TypeScript
### Example 9: Using the space and bottom APIs on the Navigation Indicator

This example uses the [bottom](#bottom19) and [space](#space19) APIs to achieve zero spacing control between the dot-style navigation indicators and the bottom, as well as spacing control between navigation indicators.


```

```TypeScript
### Example 10: Displaying the Number of Elements Displayed in the Swiper Component Based on Breakpoints

This example demonstrates how to set the number of elements displayed in the Swiper viewport based on breakpoints.

Since API version 22, the [displaycount](arkts-arkui-swiper-comp-attribute.md#displaycount) API is added to set the number of elements displayed in the Swiper viewport.

When the Swiper width falls within the [sm](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) and smaller breakpoint range, one column is displayed.



When the Swiper width falls within the [md](../../../ui/arkts-layout-development-grid-layout.md#breakpoints), two columns are displayed.


```

```TypeScript
### Example 11: Implementing Drag Simulation Using the Swiper Component

This example shows how to implement drag simulation using the Swiper component. If the component itself does not respond to the drag event, the child component Column invokes the Swiper API based on the touch event information to implement a similar effect to that of dragging.

Since API version 23, the [startFakeDrag](arkts-arkui-swipercontroller-c.md#startfakedrag), [fakeDragBy](arkts-arkui-swipercontroller-c.md#fakedragby), [stopFakeDrag](arkts-arkui-swipercontroller-c.md#stopfakedrag), and [isFakeDragging](arkts-arkui-swipercontroller-c.md#isfakedragging) APIs are added to implement drag simulation.


```

```TypeScript
### Example 12: Configuring the Navigation Dot Icon of the Swiper Component

This example shows how to configure the navigation dot icon of the Swiper component by setting the indicatorIcon API.

Since API version 26.0.0, the [indicatorIcon](arkts-arkui-dotindicator-c.md#indicatoricon) API is added.
```
