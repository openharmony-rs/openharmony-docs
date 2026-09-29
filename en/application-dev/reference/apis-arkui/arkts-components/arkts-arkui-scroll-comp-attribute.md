# Scroll properties/events

```TypeScript
declare class ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>
```

In addition to [universal attributes](arkts-arkui-common-comp.md) and [scrollable component common attributes](arkts-arkui-common-comp-scrollablecommonmethod-c.md), the following attributes are also supported.

In addition to [universal events](arkts-arkui-common-comp.md) and [scrollable component common events](arkts-arkui-common-comp-scrollablecommonmethod-c.md), the following events are also supported.

**Inheritance/Implementation:** ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>

**Since:** 7

<!--Device-unnamed-declare class ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>--><!--Device-unnamed-declare class ScrollAttribute extends ScrollableCommonMethod<ScrollAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## edgeEffect

```TypeScript
edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions)
```

Sets the effect used when the scroll boundary is reached.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): ScrollAttribute--><!--Device-ScrollAttribute-edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| edgeEffect | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.None** |
| options | [EdgeEffectOptions](arkts-arkui-common-comp-edgeeffectoptions-i.md) | No | Whether to enable the effect when the component content is smaller than the component itself. The value **{ alwaysEnabled: true }** enables the sliding effect, and **{ alwaysEnabled: false }** disables it. When not passed, the default value is used.<br>Default value: **{ alwaysEnabled: true }**<br><br>**Since:** 11 |

## enableBouncesZoom

```TypeScript
enableBouncesZoom(enable: boolean)
```

Sets whether to enable the zoom bounce effect.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-enableBouncesZoom(enable: boolean): ScrollAttribute--><!--Device-ScrollAttribute-enableBouncesZoom(enable: boolean): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to enable the zoom bounce effect. When the user zooms beyond the maximum or minimum zoom ratio, the content bounces back to the maximum or minimum zoom ratio after the gesture is released. The value **true** means to enable the effect, and **false** means to disable it.<br>Default value: **true** |

## enablePaging

```TypeScript
enablePaging(value: boolean)
```

Sets whether to enable swipe paging. If both swipe paging (**enablePaging**) and **scrollSnap** are set, **scrollSnap** takes effect first and **enablePaging** does not take effect. This attribute can be used in scenarios such as book page turning and card paging browsing.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollAttribute-enablePaging(value: boolean): ScrollAttribute--><!--Device-ScrollAttribute-enablePaging(value: boolean): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support swipe paging. The value **true** means that swipe paging is supported, and **false** means the opposite.<br>Default value: **false** |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

Sets whether to support scroll gestures. It can be used to temporarily disable user gesture scrolling of the scroll component in scenarios where services such as custom dragging and custom scrolling need to take over the swipe gesture.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-enableScrollInteraction(value: boolean): ScrollAttribute--><!--Device-ScrollAttribute-enableScrollInteraction(value: boolean): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable scroll gestures. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the [Scroller](arkts-arkui-scroll-comp-scroller-c.md). <br>Default value: **true** |

## friction

```TypeScript
friction(value: number | Resource)
```

Sets the friction coefficient. It takes effect when the scroll area is swiped, and affects only the inertial scrolling process. It has an indirect impact on the chained effect during inertial scrolling.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-friction(value: number | Resource): ScrollAttribute--><!--Device-ScrollAttribute-friction(value: number | Resource): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.9** for wearable devices and **0.6** for non-wearable devices <br>Since API version 11, the default value for non-wearable devices is **0.7**. <br>Since API version 12, the default value for non-wearable devices is **0.75**. <br>Value range: (0, +∞). If the value is less than or equal to 0, the default value is used. |

## initialOffset

```TypeScript
initialOffset(value: OffsetOptions)
```

Sets the initial scroll offset. It takes effect only during the first layout, and subsequent dynamic changes to this attribute value do not take effect. It can be used to locate a specified scroll position when the page is displayed for the first time.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollAttribute-initialOffset(value: OffsetOptions): ScrollAttribute--><!--Device-ScrollAttribute-initialOffset(value: OffsetOptions): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [OffsetOptions](arkts-arkui-scroll-comp-offsetoptions-i.md) | Yes | Initial scrolling offset. When the value specified is a percentage, the initial scrolling offset is calculated as the product of the **Scroll** component's size in the main axis direction and the percentage value. |

## maxZoomScale

```TypeScript
maxZoomScale(scale: number)
```

Sets the maximum gesture-based zoom scale for the **Scroll** component's content.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-maxZoomScale(scale: number): ScrollAttribute--><!--Device-ScrollAttribute-maxZoomScale(scale: number): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Maximum gesture-based zoom scale for the **Scroll** component's content.<br>Default value: **1**. <br>Value range: (0, +∞). If the value is less than or equal to 0, the default value 1 is used. |

## minZoomScale

```TypeScript
minZoomScale(scale: number)
```

Sets the minimum gesture-based zoom scale for the **Scroll** component's content.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-minZoomScale(scale: number): ScrollAttribute--><!--Device-ScrollAttribute-minZoomScale(scale: number): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Minimum gesture-based zoom scale for the **Scroll** component's content.<br>Default value: **1**. <br>Value range: (0, maxZoomScale]. If the value is less than or equal to 0, the default value **1** is used. If the value is greater than **maxZoomScale**, **maxZoomScale** is used. |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

Sets the nested scroll mode in both forward and backward directions to implement scroll linkage with the parent component. It is applicable to nested scroll scenarios such as linkage between a list in a page and an outer scroll area.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-nestedScroll(value: NestedScrollOptions): ScrollAttribute--><!--Device-ScrollAttribute-nestedScroll(value: NestedScrollOptions): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | Nested scroll options, used to configure the nested scroll modes in the forward and backward directions, including the **scrollForward** (forward scroll mode) and **scrollBackward** (backward scroll mode) fields. **NestedScrollMode.SELF_ONLY** indicates that only the component itself scrolls, **NestedScrollMode.SELF_FIRST** indicates that the component itself scrolls first, **NestedScrollMode.PARENT_FIRST** indicates that the parent component scrolls first, and **NestedScrollMode.PARALLEL** indicates that the component itself and the parent component scroll simultaneously.<br>Default value: **{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }**<br>When **Scroll** sets [enablePaging](#enablepaging) or [scrollSnap](#scrollsnap) and also sets parent-first nested scroll, the nested scroll does not take effect. |

## onDidScroll

```TypeScript
onDidScroll(handler: ScrollOnScrollCallback)
```

Triggered when the **Scroll** component scrolls.

The return value is the scrolling offset amount in the current frame, along with the current scroll state.

Trigger conditions:

1. Triggered when the scroll component triggers scrolling. It supports keyboard and mouse operations and other
input settings that trigger scrolling.
2. The scroll controller API is called.
3. The out-of-bounds bounce effect is active.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollAttribute-onDidScroll(handler: ScrollOnScrollCallback): ScrollAttribute--><!--Device-ScrollAttribute-onDidScroll(handler: ScrollOnScrollCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [ScrollOnScrollCallback](arkts-arkui-scroll-comp-scrollonscrollcallback-t.md) | Yes | Represents the callback triggered when the **Scroll** component scrolls. |

## onDidZoom

```TypeScript
onDidZoom(event: ScrollOnDidZoomCallback)
```

Triggered when the zoom operation of each frame is completed.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-onDidZoom(event: ScrollOnDidZoomCallback): ScrollAttribute--><!--Device-ScrollAttribute-onDidZoom(event: ScrollOnDidZoomCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [ScrollOnDidZoomCallback](arkts-arkui-scroll-comp-scrollondidzoomcallback-t.md) | Yes | Callback triggered when the zoom operation of each frame is completed. |

## onScrollEdge

```TypeScript
onScrollEdge(event: OnScrollEdgeCallback)
```

Triggered when scrolling reaches the edge.

Trigger conditions:

1. Triggered when the scroll component scrolls to the edge. It supports keyboard and mouse operations and other
input settings that trigger scrolling.
2. The scroll controller API is called.
3. The out-of-bounds bounce effect is active.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-onScrollEdge(event: OnScrollEdgeCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollEdge(event: OnScrollEdgeCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnScrollEdgeCallback](arkts-arkui-scroll-comp-onscrolledgecallback-t.md) | Yes | Edge position to scroll to. <br>For horizontal scrolling, [Edge.Center](../arkts-apis/arkts-arkui-edge-e.md) represents the start position, and [Edge.Baseline](../arkts-apis/arkts-arkui-edge-e.md) represents the end position. Note: The enum values [Edge.Center](../arkts-apis/arkts-arkui-edge-e.md) and [Edge.Baseline](../arkts-apis/arkts-arkui-edge-e.md) are deprecated. You are advised to use the onReachStart and onReachEnd to detect when the component reaches its boundary.<br>**Since:** 18 |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

Triggered at the beginning of each scroll frame. The event parameter provides the pending scroll offset. The event handler can calculate the actual scroll amount based on the use case and return this value as its result. The **Scroll** component then scrolls according to the returned actual scroll amount.

The value of [offsetRemain](arkts-arkui-scroll-comp-onscrollframebeginhandlerresult-i.md) can be negative.

If the **onScrollFrameBegin** event and [scrollBy](arkts-arkui-scroll-comp-scroller-c.md#scrollby) method are used to implement nested scrolling, set the [EdgeEffect](#edgeeffect) attribute of the scrollable child component to **None**. For example, if a **List** component is nested in the **Scroll** container, [edgeEffect](arkts-arkui-list-comp-attribute.md#edgeeffect) of the **List** component must be set to **EdgeEffect.None**. Otherwise, swiping the **List** triggers its edge bounce animation, which results in failed nested scrolling.

This event is triggered when any of the following conditions is met:

1. Scrolling is initiated by user interaction (for example, finger swipe, keyboard, or mouse operation).
2. The **Scroll** component scrolls by inertia.
3. Scrolling is triggered by calling the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) API.

This event is not triggered when any of the following conditions is met:

1. A scroll control API other than [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) is called.
2. The out-of-bounds bounce effect is active.
3. The scrollbar is dragged.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-scroll-comp-onscrollframebegincallback-t.md) | Yes | Callback triggered when each frame scrolling starts.<br>**Since:** 18 |

## onScrollStart

```TypeScript
onScrollStart(event: VoidCallback)
```

Triggered when scrolling starts and is initiated by the user's finger dragging the **Scroll** component or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) starts.

Trigger conditions:

1. Triggered when the scroll component starts scrolling. It supports keyboard and mouse operations and other input
settings that trigger scrolling.
2. The scroll controller API is called and then starts, with a transition animation.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-onScrollStart(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollStart(event: VoidCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback triggered when scrolling starts.<br>**Since:** 18 |

## onScrollStop

```TypeScript
onScrollStop(event: VoidCallback)
```

Triggered when scrolling stops after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) stops.

Trigger conditions:

1. Triggered when the scroll component stops after scrolling is triggered. It supports keyboard and mouse
operations and other input settings that trigger scrolling.
2. The scroll controller API is called and then starts, with a transition animation.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-onScrollStop(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onScrollStop(event: VoidCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback triggered when scrolling stops.<br>**Since:** 18 |

## onWillScroll

```TypeScript
onWillScroll(handler: ScrollOnWillScrollCallback)
```

Triggered before scrolling.

The callback provides the amount of offset that is about to be scrolled in the current frame, along with the current scroll status and the source of the scrolling operation. The offset provided in the callback is the calculated intended scrolling offset, not the final actual scrolling offset. You can specify the intended scrolling offset for the **Scroll** through the return value of this callback.

Trigger conditions:

1. Triggered when the scroll component triggers scrolling. It supports keyboard and mouse operations and other
input settings that trigger scrolling.
2. The scroll controller API is called.
3. The out-of-bounds bounce effect is active.

> **NOTE:** 
> 
> The scrolling event callback is triggered frequently during scrolling. To avoid frame freezing or dropped frames,
> do not perform time-consuming operations in this callback. For best practices, see
> [High-Frequency Callback Scenarios]
> (https://developer.huawei.com/consumer/en/doc/best-practices/bpta-time-optimization-of-the-main-thread
> #section10112623611).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ScrollAttribute-onWillScroll(handler: ScrollOnWillScrollCallback): ScrollAttribute--><!--Device-ScrollAttribute-onWillScroll(handler: ScrollOnWillScrollCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [ScrollOnWillScrollCallback](arkts-arkui-scroll-comp-scrollonwillscrollcallback-t.md) | Yes | Callback triggered before scrolling. |

## onZoomStart

```TypeScript
onZoomStart(event: VoidCallback)
```

Triggered when a zoom gesture starts.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-onZoomStart(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onZoomStart(event: VoidCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback triggered when the zoom gesture starts. |

## onZoomStop

```TypeScript
onZoomStop(event: VoidCallback)
```

Triggered when a zoom gesture stops.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-onZoomStop(event: VoidCallback): ScrollAttribute--><!--Device-ScrollAttribute-onZoomStop(event: VoidCallback): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [VoidCallback](../arkts-apis/arkts-arkui-voidcallback-t.md) | Yes | Callback triggered when the zoom gesture stops. |

## scrollable

```TypeScript
scrollable(value: ScrollDirection)
```

Sets the scroll direction. After this value is modified, the scroll offset is reset. You can select vertical scroll, horizontal scroll, or free scroll based on the layout.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-scrollable(value: ScrollDirection): ScrollAttribute--><!--Device-ScrollAttribute-scrollable(value: ScrollDirection): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScrollDirection](arkts-arkui-scroll-comp-scrolldirection-e.md) | Yes | Scrolling direction.<br>Default value: **ScrollDirection.Vertical** |

## scrollBar

```TypeScript
scrollBar(barState: BarState)
```

Sets the scroll bar state. If the container component cannot scroll, the scroll bar is not displayed. If the size of the child component of the container component is infinite, the scroll bar does not support dragging and accompanying scrolling. This attribute can be used to control whether the scroll bar is always displayed, automatically displayed, or hidden.

Since API version 10, when the scrollable component has rounded corners, to prevent the scrollbar from being cut off by the corners, the scrollbar will automatically calculate the clearance distance from the top and bottom.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-scrollBar(barState: BarState): ScrollAttribute--><!--Device-ScrollAttribute-scrollBar(barState: BarState): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| barState | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Scrollbar state.<br>Default value: **BarState.Auto** |

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string)
```

Sets the scrollbar color.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string | Yes | Scrollbar color.<br>Default value: **'#66182431'** <br>A number value indicates a HEX color in RGB or ARGB format, value range: [0x0, 0xFFFFFFFF], for example, **0xffffff**. <br>A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**. |

<a id="scrollbarcolor-1"></a>

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource)
```

Sets the scrollbar color. Compared with [scrollBarColor](#scrollbarcolor), this API supports the Resource type for the **color** parameter.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string | Resource): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarColor(color: Color | number | string | Resource): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar color.<br>Default value: **'#66182431'**<br>A number value indicates a HEX color in RGB or ARGB format, with a value range of [0x0, 0xFFFFFFFF], for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**. |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string)
```

Sets the width of the scroll bar. Percentage values are not supported. After the width is set, the scroll bar width in both the normal state and the pressed state is the set value. If the scroll bar width exceeds the visible size of the **Scroll** component along the main axis, the default value of 4 vp is used.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-scrollBarWidth(value: number | string): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarWidth(value: number | string): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Width of the scrollbar.<br>Default value: **4**<br>Unit: vp <br>Value range: If the value is less than 0, the default value 4 vp is used. If the value is 0, the scrollbar is not displayed. |

<a id="scrollbarwidth-1"></a>

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource)
```

Sets the width of the scrollbar. Percentage values are not supported. After the width is set, the scrollbar width in both the normal state and the pressed state is the set value. If the scrollbar width exceeds the visible size of the **Scroll** component along the main axis, the scrollbar width changes to the default value of 4 vp. Resource type is supported.

If this attribute is not set, the scrollbar width is 4 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ScrollAttribute-scrollBarWidth(value: number | string | Resource): ScrollAttribute--><!--Device-ScrollAttribute-scrollBarWidth(value: number | string | Resource): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar width.<br>Default value: **4**<br>Unit: vp <br>The value range is [0, +∞). If this parameter is set to a value less than 0, the default value **4vp** is used. The value **0** means not to show the scrollbar. |

## scrollSnap

```TypeScript
scrollSnap(value: ScrollSnapOptions)
```

Sets the scroll snap mode of the **Scroll** component, which is used to implement scenarios such as paging scroll and card alignment that require positioning to a specified position after scrolling ends.

During the snap animation, the scroll operation source type reported by the [onWillScroll](#onwillscroll) event is **ScrollSource.FLING**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-scrollSnap(value: ScrollSnapOptions): ScrollAttribute--><!--Device-ScrollAttribute-scrollSnap(value: ScrollSnapOptions): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScrollSnapOptions](arkts-arkui-scroll-comp-scrollsnapoptions-i.md) | Yes | Scroll snap mode of the **Scroll** component. This object contains attributes such as **snapAlign** (alignment), **snapPagination** (pagination), **enableSnapToStart** (whether to snap to the start), and **enableSnapToEnd** (whether to snap to the end). |

## zoomScale

```TypeScript
zoomScale(scale: number)
```

Sets the zoom scale of the **Scroll** component's content.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ScrollAttribute-zoomScale(scale: number): ScrollAttribute--><!--Device-ScrollAttribute-zoomScale(scale: number): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| scale | number | Yes | Zoom scale of the **Scroll** component's content. This parameter supports two-way binding through [!!](../../../ui/state-management/arkts-new-binding.md). <br>Default value: **1**. <br>Value range: (0, +∞). If the value is less than or equal to 0, the default value 1 is used. |

## onScroll

```TypeScript
onScroll(event: (xOffset: number, yOffset: number) => void)
```

Triggered to return the horizontal and vertical offsets, in vp, during scrolling when the specified scroll event occurs.

Trigger conditions:

1. Triggered when the scroll component triggers scrolling. It supports keyboard and mouse operations and other
input settings that trigger scrolling.
2. The scroll controller API is called.
3. The out-of-bounds bounce effect is active.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** onWillScroll

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ScrollAttribute-onScroll(event: (xOffset: number, yOffset: number) => void): ScrollAttribute--><!--Device-ScrollAttribute-onScroll(event: (xOffset: number, yOffset: number) => void): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (xOffset: number, yOffset: number) =&gt; void | Yes | callback when scroll, xOffset: Actual scroll offset relative to the previous frame.<br>Unit: vp yOffset: Vertical offset relative to the previous frame. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward. <br>Unit: vp |

## onScrollEnd

```TypeScript
onScrollEnd(event: () => void)
```

Triggered when scrolling stops.

Trigger conditions:

1. Triggered when the scroll component stops after scrolling is triggered. It supports keyboard and mouse
operations and other input settings that trigger scrolling.
2. The scroll controller API is called and then stops, with a transition animation.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** onScrollStop

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ScrollAttribute-onScrollEnd(event: () => void): ScrollAttribute--><!--Device-ScrollAttribute-onScrollEnd(event: () => void): ScrollAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when scrolling stops. |
