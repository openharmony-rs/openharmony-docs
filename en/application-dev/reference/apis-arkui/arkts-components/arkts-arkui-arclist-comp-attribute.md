# ArcList properties/events

```TypeScript
export declare class ArcListAttribute extends CommonMethod<ArcListAttribute>
```

In addition to the universal attributes, the following attributes are supported (the [scrollable component common attributes](arkts-arkui-common-comp-scrollablecommonmethod-c.md) are not supported):

**Inheritance/Implementation:** ArcListAttribute extends CommonMethod<ArcListAttribute>

**Since:** 18

<!--Device-unnamed-export declare class ArcListAttribute extends CommonMethod<ArcListAttribute>--><!--Device-unnamed-export declare class ArcListAttribute extends CommonMethod<ArcListAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## cachedCount

```TypeScript
cachedCount(count: Optional<number>)
```

Sets the number of arc list items to be preloaded (cached). In a lazy loading scenario, only the content equivalent to **cachedCount** outside the visible area of the arc list is preloaded. In a non-lazy loading scenario, all items are loaded at once. For both lazy and non-lazy loading, only the content within the visible area of the arc list plus the content equivalent to **cachedCount** outside the visible area is laid out.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-cachedCount(count: Optional<number>): ArcListAttribute--><!--Device-ArcListAttribute-cachedCount(count: Optional<number>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Number of **ArcListItem** items to preload.<br>Default value: set based on the number of nodes displayed on the screen, with a maximum of 16. <br>Value range: [0, +∞) <br>If this parameter is set to a negative number, **1** is used. |

## chainAnimation

```TypeScript
chainAnimation(enable: Optional<boolean>)
```

Sets whether to enable chained animations, which provide a visually connected, or "chained," effect when the **ArcList** component is scrolled or its top or bottom edge is dragged.

The list items are separated with even space, and one item animation starts after the previous animation during basic sliding interactions. The chained animation effect is similar with spring physics.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-chainAnimation(enable: Optional<boolean>): ArcListAttribute--><!--Device-ArcListAttribute-chainAnimation(enable: Optional<boolean>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the chained linkage effect. The chained linkage effect takes effect only when the edge effect is [EdgeEffect.Spring](../arkts-apis/arkts-arkui-edgeeffect-e.md#spring). <br>Default value: **false**, the chained linkage is not enabled; **true**, the chained linkage is enabled. |

## childrenMainSize

```TypeScript
childrenMainSize(size: Optional<ChildrenMainSize>)
```

Sets the size information of the child components of the **ArcList** component along the main axis.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-childrenMainSize(size: Optional<ChildrenMainSize>): ArcListAttribute--><!--Device-ArcListAttribute-childrenMainSize(size: Optional<ChildrenMainSize>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ChildrenMainSize](arkts-arkui-common-comp-childrenmainsize-c.md)&gt; | Yes | Provides precise size information of all child components in the main axis direction to the **ArcList** component through the [ChildrenMainSize](arkts-arkui-common-comp-childrenmainsize-c.md) object. This ensures that the **ArcList** component can maintain the accuracy of its scroll position in scenarios such as inconsistent child component main axis sizes, addition or removal of child components, and when using [scrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex). It further guarantees that [scrollTo](arkts-arkui-scroll-comp-scroller-c.md#scrollto) can accurately jump to the specified position, [currentOffset](arkts-arkui-scroll-comp-scroller-c.md#currentoffset) or [offset](arkts-arkui-scroll-comp-scroller-c.md#offset) accurately reflects the current scroll position, and the built-in scrollbar can move smoothly without any jumps or abrupt changes. Since API version 23, the **offset** API is added. <br> **NOTE:** <br>The provided main axis size must be consistent with the actual main axis size of the child components. Otherwise, the **ArcList** component may display abnormally. When the main axis size of a child component changes or when child components are added or removed, the **ArcList** component must be notified of the changes by calling the methods of the **ChildrenMainSize** object. Otherwise, the **ArcList** component may display abnormally. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the crown response sensitivity.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcListAttribute--><!--Device-ArcListAttribute-digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Crown response sensitivity.<br>Default value: **CrownSensitivity.MEDIUM**, which indicates a moderate response speed. |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(enable: Optional<boolean>)
```

Sets whether to enable scroll gestures.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-enableScrollInteraction(enable: Optional<boolean>): ArcListAttribute--><!--Device-ArcListAttribute-enableScrollInteraction(enable: Optional<boolean>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to support the scroll gesture. When set to **true**, the list can be scrolled by finger or mouse. When set to **false**, the list cannot be scrolled by finger or mouse, but the scrolling API of the [Scroller](arkts-arkui-scroll-comp-scroller-c.md) controller is not affected. <br>Default value: **true** |

## fadingEdge

```TypeScript
fadingEdge(enable: Optional<boolean>)
```

Sets whether to enable the edge fading effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-fadingEdge(enable: Optional<boolean>): ArcListAttribute--><!--Device-ArcListAttribute-fadingEdge(enable: Optional<boolean>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the edge fading effect. <br>When **fadingEdge** takes effect, it overrides the `.overlay()` attribute of the original component. <br>When **fadingEdge** takes effect, it is recommended not to set background-related attributes on this component, as they may affect the fading display effect. <br>When **fadingEdge** takes effect, the component is clipped to the boundary, and setting the component's [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) attribute to **false** does not take effect. <br>The value **true** enables the edge fading effect, and **false** disables it. <br>Default value: **false** |

## flingSpeedLimit

```TypeScript
flingSpeedLimit(speed: Optional<number>)
```

Sets the maximum initial speed for inertial scrolling after a fling gesture. If this attribute is set to a value less than or equal to 0, the default value is used.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-flingSpeedLimit(speed: Optional<number>): ArcListAttribute--><!--Device-ArcListAttribute-flingSpeedLimit(speed: Optional<number>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Maximum initial speed when the inertial scrolling animation starts. If this parameter is set to a value less than or equal to 0, the default value is used.<br>Default value: **9000** <br>Unit: vp/s <br>Value range: (0, +∞) <br>The abnormal values **undefined** and **null** are treated as invalid values, and this setting does not take effect. |

## friction

```TypeScript
friction(friction: Optional<number>)
```

Sets the friction coefficient, which takes effect when manually swiping the scroll area and only affects the inertial scrolling process. If the value is set to 0 or less, the default value is used.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-friction(friction: Optional<number>): ArcListAttribute--><!--Device-ArcListAttribute-friction(friction: Optional<number>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| friction | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Friction coefficient. It takes effect when manually swiping the scroll area and affects only the inertial scrolling process. If set to a value less than or equal to 0, the default value is used.<br>Default value: **0.8** <br>Value range: (0, +∞) |

## onDidScroll

```TypeScript
onDidScroll(handler: Optional<OnScrollCallback>)
```

Triggered when the list scrolls. The return value is the offset amount by which the list has scrolled and the current scroll state.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onDidScroll(handler: Optional<OnScrollCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onDidScroll(handler: Optional<OnScrollCallback>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md)&gt; | Yes | Callback triggered when the list scrolls. |

## onReachEnd

```TypeScript
onReachEnd(handler: Optional<VoidCallback>)
```

Triggered when the list reaches the end position.

When the edge effect of **ArcList** is set to the spring effect, this event is triggered once when swiping past the end position, and triggered again when the list springs back to the end position.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onReachEnd(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onReachEnd(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list reaches the end position. |

## onReachStart

```TypeScript
onReachStart(handler: Optional<VoidCallback>)
```

Triggered when the list reaches the start position.

This event is triggered during initialization of the **ArcList** component if [initialIndex](arkts-arkui-arclist-comp-arklistoptions-i.md) is set to **0**, and whenever the list scrolls to the start position. If the edge scrolling effect is set to spring, this event is triggered when scrolling past the start position and again when bouncing back to it.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onReachStart(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onReachStart(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list reaches the start position. |

## onScrollIndex

```TypeScript
onScrollIndex(handler: Optional<ArcScrollIndexHandler>)
```

Triggered when a child component enters or leaves the visible area of the **ArcList** component. This event is triggered during initialization of the **ArcList** component and when the index of the first or last child component in the visible area changes, or when the center child component changes.

When the edge effect of **ArcList** is set to the spring effect, the **onScrollIndex** event is not triggered during the process of continuing to swipe after the **ArcList** reaches the edge and during the spring-back process after release.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onScrollIndex(handler: Optional<ArcScrollIndexHandler>): ArcListAttribute--><!--Device-ArcListAttribute-onScrollIndex(handler: Optional<ArcScrollIndexHandler>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ArcScrollIndexHandler](arkts-arkui-arclist-comp-arcscrollindexhandler-t.md)&gt; | Yes | Callback triggered when a child component enters or leaves the visible area of the **ArcList** component. |

## onScrollStart

```TypeScript
onScrollStart(handler: Optional<VoidCallback>)
```

Triggered when the list starts scrolling initiated by the user's finger dragging the list or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) starts.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onScrollStart(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onScrollStart(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list starts scrolling. |

## onScrollStop

```TypeScript
onScrollStop(handler: Optional<VoidCallback>)
```

Triggered when the list stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) stops.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onScrollStop(handler: Optional<VoidCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onScrollStop(handler: Optional<VoidCallback>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list stops scrolling. |

## onWillScroll

```TypeScript
onWillScroll(handler: Optional<OnWillScrollCallback>)
```

Triggered before each frame during list scrolling. The callback returns the offset amount by which the list will scroll and the current scroll state. The returned offset is a calculated value, not the actual offset.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-onWillScroll(handler: Optional<OnWillScrollCallback>): ArcListAttribute--><!--Device-ArcListAttribute-onWillScroll(handler: Optional<OnWillScrollCallback>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnWillScrollCallback](arkts-arkui-common-comp-onwillscrollcallback-t.md)&gt; | Yes | Callback triggered before each frame during list scrolling. |

## scrollBar

```TypeScript
scrollBar(status: Optional<BarState>)
```

Sets the state of the scrollbar.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-scrollBar(status: Optional<BarState>): ArcListAttribute--><!--Device-ArcListAttribute-scrollBar(status: Optional<BarState>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BarState](../arkts-apis/arkts-arkui-barstate-e.md)&gt; | Yes | Scroll bar status.<br>Default value: **BarState.Auto** |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

Sets the color of the scrollbar.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-scrollBarColor(color: Optional<ColorMetrics>): ArcListAttribute--><!--Device-ArcListAttribute-scrollBarColor(color: Optional<ColorMetrics>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Scrollbar color.<br>Default value: **ColorMetrics.numeric(0xA9FFFFFF)** <br>The abnormal values **undefined** and **null** are treated as invalid values, and this setting does not take effect. |

## scrollBarWidth

```TypeScript
scrollBarWidth(width: Optional<LengthMetrics>)
```

Sets the width of the **ArcList** scrollbar in the pressed state. If not set, the pressed state width is **LengthMetrics.vp(24)**. The non-pressed state width is fixed at **LengthMetrics.vp(4)** and is not affected by this attribute.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-scrollBarWidth(width: Optional<LengthMetrics>): ArcListAttribute--><!--Device-ArcListAttribute-scrollBarWidth(width: Optional<LengthMetrics>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Width of the **ArcList** scrollbar in the pressed state.<br>Default value: **LengthMetrics.vp(24)** <br>Width in the unpressed state: **LengthMetrics.vp(4)** <br>If this parameter is set to an abnormal value such as a negative value or **undefined**, the width of the scrollbar in the normal state is used. <br>Unit: vp |

## space

```TypeScript
space(space: Optional<LengthMetrics>)
```

Sets the spacing between list child items.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

<!--Device-ArcListAttribute-space(space: Optional<LengthMetrics>): ArcListAttribute--><!--Device-ArcListAttribute-space(space: Optional<LengthMetrics>): ArcListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| space | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Spacing between child components in the list. <br>Default value: **LengthMetrics.vp(0)** <br>When the [visibility](arkts-arkui-common-comp-commonmethod-c.md#visibility) attribute of an **ArcList** child component is set to **None**, the child component is not displayed, but the **space** above and below it still takes effect. |
