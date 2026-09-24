# ArcList properties/events

```TypeScript
export declare class ArcListAttribute extends CommonMethod<ArcListAttribute>
```

In addition to the universal attributes, the following attributes are supported.

**Inheritance/Implementation:** ArcListAttribute extends CommonMethod<ArcListAttribute>

**Since:** 18

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

## Modules to Import

```TypeScript
import { ArcList, ArcListItem, ArcListAttribute, ArcListItemAttribute } from '@kit.ArkUI';
```

## cachedCount

```TypeScript
cachedCount(count: Optional<number>)
```

Sets the number of arc list items to be preloaded (cached). In a lazy loading scenario, only the content equivalent to **cachedCount** outside the visible area of the arc list is preloaded. In a non-lazy loading scenario, all items are loaded at once. For both lazy and non-lazy loading, only the content within the visible area of the arc list plus the content equivalent to **cachedCount** outside the visible area is laid out. When **cachedCount** is set for the arc list, the system preloads and lays out the **cachedCount**-specified number of rows of arc list items both above and below the currently visible area of the arc list.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Number of list items to preload.<br> Default value: number of nodes visible on the screen, with the maximum value of 16.<br> Value range: [0, +∞) |

## chainAnimation

```TypeScript
chainAnimation(enable: Optional<boolean>)
```

Sets whether to enable chained animations, which provide a visually connected, or"chained," effect when the **ArcList** component is scrolled or its top or bottom edge is dragged. The list items are separated with even space, and one item animation starts after the previous animation during basic sliding interactions. The chained animation effect is similar with spring physics. For chained animations to work properly, the edge scrolling effect of the **ArcList** component must be set to **EdgeEffect.Spring**.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable chained animations.<br> **false** (default): Chained animations are disabled. **true**: Chained animations are enabled. |

## childrenMainSize

```TypeScript
childrenMainSize(size: Optional<ChildrenMainSize>)
```

Sets the size information of the child components of the **ArcList** component along the main axis.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| size | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ChildrenMainSize](arkts-arkui-common-comp-childrenmainsize-c.md)&gt; | Yes | Precise size information for all child components along the main axis. This ensures accurate scrolling positions in scenarios where child components have varying sizes, are added or removed, or when APIs like **scrollToIndex** are used. It guarantees that **scrollTo** can accurately navigate to the specified position, **currentOffset** or **offset** can accurately reflect the current scrolling position, and the built-in scrollbar can move smoothly without any jumps or abrupt changes. The **offset** API is added from API version 23.<br> **NOTE:** <br>The provided sizes must match the actual sizes of the child components. Any changes to the sizes, or any additions or removals of child components, must be notified to the **ArcList** component through the **ChildrenMainSize** object. |

## digitalCrownSensitivity

```TypeScript
digitalCrownSensitivity(sensitivity: Optional<CrownSensitivity>)
```

Sets the sensitivity of the digital crown's event response.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sensitivity | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[CrownSensitivity](../arkts-apis/arkts-arkui-crownsensitivity-e.md)&gt; | Yes | Sensitivity of the digital crown's event response.<br>Default value: **CrownSensitivity.MEDIUM**, indicating moderate response speed. |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(enable: Optional<boolean>)
```

Sets whether to enable scroll gestures.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable scroll gestures. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the **Scroller**.<br>Default value: **true** |

## fadingEdge

```TypeScript
fadingEdge(enable: Optional<boolean>)
```

Sets whether to enable the edge fading effect.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;boolean&gt; | Yes | Whether to enable the edge fading effect.<br> When **fadingEdge** is set to **true**, it overrides the **.overlay()** attribute of the component.<br>With **fadingEdge** set to **true**, avoid setting background-related attributes on the component, as this may affect the display of the fading effect.<br> When **fadingEdge** is set to **true**, the component is clipped to the boundary. If the **clip** attribute of the component is set to **false**, the setting does not take effect.<br>With the value **true**, the edge fading effect is enabled. With the value **false**, the edge fading effect is disabled.<br>Default value: **false**. |

## flingSpeedLimit

```TypeScript
flingSpeedLimit(speed: Optional<number>)
```

Sets the maximum initial speed for inertial scrolling after a fling gesture. If this attribute is set to a value less than or equal to 0, the default value is used.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Maximum initial speed for inertial scrolling.<br> Default value: **9000**.<br>Unit: vp/s.<br>Value range: (0, +∞) |

## friction

```TypeScript
friction(friction: Optional<number>)
```

Sets the friction coefficient. It applies only to gestures in the scrolling area, and it affects only the inertial scrolling process. If this attribute is set to a value less than or equal to 0, the default value is used.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| friction | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;number&gt; | Yes | Friction coefficient.<br> Default value: **0.8**<br>Value range: (0, +∞) |

## onDidScroll

```TypeScript
onDidScroll(handler: Optional<OnScrollCallback>)
```

Triggered when the list scrolls. The return value is the offset amount by which the list has scrolled and the current scroll state.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[OnScrollCallback](arkts-arkui-common-comp-onscrollcallback-t.md)&gt; | Yes | Callback triggered when the list scrolls. |

## onReachEnd

```TypeScript
onReachEnd(handler: Optional<VoidCallback>)
```

Triggered when the list reaches the end position. If the edge scrolling effect is set to spring, this event is triggered when scrolling past the end position and again when bouncing back to it.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list reaches the end position. |

## onReachStart

```TypeScript
onReachStart(handler: Optional<VoidCallback>)
```

Triggered when the list reaches the start position. This event is triggered during initialization of the **ArcList** component if **initialIndex** is set to **0**, and whenever the list scrolls to the start position. If the edge scrolling effect is set to spring, this event is triggered when scrolling past the start position and again when bouncing back to it.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list reaches the start position. |

## onScrollIndex

```TypeScript
onScrollIndex(handler: Optional<ArcScrollIndexHandler>)
```

Triggered when a child component enters or leaves the visible area of the **ArcList** component. This event is triggered during initialization of the **ArcList** component and when the index of the first or last child component in the visible area changes, or when the center child component changes. If the edge scrolling effect of the **ArcList** component is set to spring, this event is not triggered during continued scrolling at the edge or during the bounce-back process.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[ArcScrollIndexHandler](arkts-arkui-arclist-comp-arcscrollindexhandler-t.md)&gt; | Yes | Callback triggered when a child component enters or leaves the visible area of the **ArcList** component. |

## onScrollStart

```TypeScript
onScrollStart(handler: Optional<VoidCallback>)
```

Triggered when the list starts scrolling initiated by the user's finger dragging the list or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by **Scroller** starts.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md)&gt; | Yes | Callback triggered when the list starts scrolling. |

## onScrollStop

```TypeScript
onScrollStop(handler: Optional<VoidCallback>)
```

Triggered when the list stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by **Scroller** stops.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| status | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[BarState](../arkts-apis/arkts-arkui-barstate-e.md)&gt; | Yes | State of the scrollbar.<br> Default value: **BarState.Auto** |

## scrollBarColor

```TypeScript
scrollBarColor(color: Optional<ColorMetrics>)
```

Sets the color of the scrollbar.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;ColorMetrics&gt; | Yes | Color of the scrollbar.<br> Default value: **ColorMetrics.numeric(0xA9FFFFFF)** |

## scrollBarWidth

```TypeScript
scrollBarWidth(width: Optional<LengthMetrics>)
```

Sets the width of the scrollbar. Once the width is set, the scrollbar will use this width in its pressed state.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| width | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Width of the scrollbar.<br> Default value: **LengthMetrics.vp(24)**.<br>Minimum value: **LengthMetrics.vp(4)**<br>Unit: vp |

## space

```TypeScript
space(space: Optional<LengthMetrics>)
```

Sets the spacing between list items.

**Since:** 18

**Atomic service API:** This API can be used in atomic services since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Circle

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| space | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;LengthMetrics&gt; | Yes | Spacing between list items.<br> Default value: **LengthMetrics.vp(0)**.<br>Child components of **ArcList** whose visibility attribute is set to **None** are not displayed, but the spacing above and below them still takes effect. |
