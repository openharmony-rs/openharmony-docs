# Scroll

Defines Scroll Component.

## Scroll

```TypeScript
Scroll(scroller?: Scroller)
```

Called when a scrollable container is set.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scroller | [Scroller](arkts-arkui-scroller-c.md) | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [OffsetOptions](arkts-arkui-offsetoptions-i.md) | Provides parameters for setting the initial scrolling offset. |
| [OffsetResult](arkts-arkui-offsetresult-i.md) | Represents the offset values resulting from a scroll operation. |
| [OnScrollFrameBeginHandlerResult](arkts-arkui-onscrollframebeginhandlerresult-i.md) | The data returned by the event handler when onScrollFrameBegin. |
| [ScrollAnimationOptions](arkts-arkui-scrollanimationoptions-i.md) | Provides parameters for customizing scroll animations. |
| [ScrollEdgeOptions](arkts-arkui-scrolledgeoptions-i.md) | Provides parameters for scrolling to the edge of a scrollable container. |
| [ScrollOptions](arkts-arkui-scrolloptions-i.md) | Provides parameters for scrolling to a specific position in a scrollable container. |
| [ScrollPageOptions](arkts-arkui-scrollpageoptions-i.md) | Provides parameters for page scrolling behavior. |
| [ScrollSnapOptions](arkts-arkui-scrollsnapoptions-i.md) | Defines a scroll snapping mode object. |
| [ScrollToIndexOptions](arkts-arkui-scrolltoindexoptions-i.md) | Provides parameters for scrolling to a specific index. |
| [UIScrollEvent](arkts-arkui-uiscrollevent-i.md) | Defines a UIScrollableCommonEvent which is used to set different common event to target component. |

### Types

| Name | Description |
| --- | --- |
| [OnScrollEdgeCallback](arkts-arkui-onscrolledgecallback-t.md) | Represents the callback triggered when scrolling reaches an edge. |
| [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | Represents the callback triggered before each frame scrolling starts. |
| [ScrollOnDidZoomCallback](arkts-arkui-scrollondidzoomcallback-t.md) | callback of Scroll, using in onDidZoom. |
| [ScrollOnScrollCallback](arkts-arkui-scrollonscrollcallback-t.md) | Represents the callback triggered when the &lt;em&gt;Scroll&lt;/em&gt; component scrolls. |
| [ScrollOnWillScrollCallback](arkts-arkui-scrollonwillscrollcallback-t.md) | Called before scroll to allow developer to control real offset the Scroll can scroll. |

### Enums

| Name | Description |
| --- | --- |
| [ScrollAlign](arkts-arkui-scrollalign-e.md) | Enumerates alignment modes. |
| [ScrollDirection](arkts-arkui-scrolldirection-e.md) | Enumerates the scrolling directions. |

## Examples

```TypeScript
### Example 1: Setting the Scroller

This example demonstrates the use of some attributes of the Scroll component and the Scroller.


```

```TypeScript
### Example 2: Implementing Nested Scrolling (Method 1)

This example uses the onScrollFrameBegin event to achieve nested scrolling between an inner List component and an outer Scroll component.


```

```TypeScript
### Example 3: Implementing Nested Scrolling (Method 2)

This example uses the [nestedScroll](#nestedscroll10) attribute to achieve nested scrolling between an inner List component and an outer Scroll component.


```

```TypeScript
### Example 4: Implementing Nested Scrolling with Parent-to-Child Scrolling Propagation

This example demonstrates how to propagate scrolling from a parent component to a child component using the [enableScrollInteraction](#enablescrollinteraction10) attribute and the [onScrollFrameBegin](#onscrollframebegin9) event.


```

```TypeScript
### Example 5: Setting Scroll Snapping

This example shows how to set scroll snapping for a Scroll component.


```

```TypeScript
### Example 6: Obtaining the Index of a Child Component

This example demonstrates how to obtain the index of a child component in a List component.


```

```TypeScript
### Example 7: Setting Edge Fading

This example demonstrates how to implement a Scroll component with an edge fading effect and set the length of the fading edge.


```

```TypeScript
### Example 8: Setting the Single-Side Edge Effect

This example demonstrates how to set a single-side edge effect for the Scroll component using the [edgeEffect](#edgeeffect) API.


```

```TypeScript
### Example 9: Implementing the Swipe-to-Turn-Pages Effect

This example demonstrates how to implement the swipe-to-turn-pages feature for a Scroll component using the [enablePaging](arkts-arkui-scroll-comp-attribute.md#enablepaging) API.


```

```TypeScript
### Example 10: Implementing the Overscroll Stay Effect

This example demonstrates how to implement the overscroll stay effect for a Scroll component using the [scrollTo](#scrollto) API.


```

```TypeScript
### Example 11: Implementing Free Scrolling and Scaling

This example demonstrates how to implement free scrolling and scaling of the Scroll component. This functionality is supported since API version 20.


```

```TypeScript
### Example 12: Obtaining the Total Content Size

This example demonstrates how to obtain the total content size. This functionality is supported since API version 22.


```

```TypeScript
### Example 13: Setting Scrolling Events

This example obtains a [UIScrollEvent](arkts-arkui-uiscrollevent-i.md) instance via getEvent('Scroll') on a FrameNode and sets scroll event callbacks for a Scroll component. This approach is intended for scenarios where the page code cannot be directly modified to use declarative callbacks.

The UIScrollEvent API is supported since API version 19.
```
