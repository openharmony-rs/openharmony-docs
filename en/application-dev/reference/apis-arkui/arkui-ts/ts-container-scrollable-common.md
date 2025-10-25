# Scrollable Component Common APIs

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @yylong; @zcdqs-->
<!--Designer: @yylong; @zcdqs-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @HelloCrease-->

The common attributes and events for scrollable components currently only support the [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), and [WaterFlow](ts-container-waterflow.md) components.

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.

## Attributes

### scrollBar<sup>11+</sup>

scrollBar(barState: BarState): T

Sets the scrollbar state.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                     | Mandatory| Description                                  |
| -------- | ----------------------------------------- | ---- | -------------------------------------- |
| barState | [BarState](ts-appendix-enums.md#barstate) | Yes  | Scrollbar state.<br>Default value: **BarState.Auto** for the **List**, **Grid**, and **Scroll** components and **BarState.Off** for the **WaterFlow** component|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### scrollBarColor<sup>11+</sup>

scrollBarColor(color: Color | number | string): T

Sets the scrollbar color.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description          |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| color  | [Color](ts-appendix-enums.md#color) \| number \| string | Yes  | Scrollbar color.<br>Default value: **'\#182431'** (40% opacity)<br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### scrollBarColor<sup>22+</sup>

scrollBarColor(color: Color | number | string | Resource): T

Sets the scrollbar color.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description          |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| color  | [Color](ts-appendix-enums.md#color) \| number \| string \| [Resource](ts-types.md#resource) | Yes  | Scrollbar color.<br>Default value: **'\#182431'** (40% opacity)<br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### scrollBarWidth<sup>11+</sup>

scrollBarWidth(value: number | string): T

Sets the scrollbar width. This attribute cannot be set in percentage. After the width is set, the scrollbar is displayed with the set width in normal state and pressed state. If the set width exceeds the height of the scrollable component on the main axis, the scrollbar reverts to the default width.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                      | Mandatory| Description                                     |
| ------ | -------------------------- | ---- | ----------------------------------------- |
| value  | number \| string | Yes  | Scrollbar width.<br>Default value: **4**<br>Unit: vp<br>If this parameter is set to a value less than or equal to 0, the default value is used. The value **0** means not to show the scrollbar.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### edgeEffect<sup>11+</sup>

edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions): T

Sets the effect used when the scroll boundary is reached.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                                             | Mandatory| Description                                                        |
| --------------------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| edgeEffect            | [EdgeEffect](ts-appendix-enums.md#edgeeffect)     | Yes  | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.None** for the **Grid**, **Scroll**, and **WaterFlow** components and **EdgeEffect.Spring** for the **List** component|
| options | [EdgeEffectOptions](#edgeeffectoptions11) | No  | Whether to enable the sliding effect when the component content size is smaller than the component size, and the edge where the edge effect takes effect. The value **{ alwaysEnabled: true }** means to enable the scroll effect, and **{ alwaysEnabled: false }** means the opposite.<br>Default value:<br>List, Grid, and WaterFlow components: { alwaysEnabled: false, EffectEdge: EffectEdge.START \| EffectEdge.END }, Scroll component: { alwaysEnabled: true, EffectEdge: EffectEdge.START \| EffectEdge.END }.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### nestedScroll<sup>11+</sup>

nestedScroll(value: NestedScrollOptions): T

Sets the nested scrolling mode in the forward and backward directions to implement scrolling association with the parent component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                 | Mandatory| Description          |
| ------ | ----------------------------------------------------- | ---- | -------------- |
| value  | [NestedScrollOptions](#nestedscrolloptions10) | Yes  | Nested scrolling options.<br>Default value: { scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### enableScrollInteraction<sup>11+</sup>

enableScrollInteraction(value: boolean): T

Sets whether to support the scrolling gesture.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                               |
| ------ | ------- | ---- | ----------------------------------- |
| value  | boolean | Yes  | Whether to support scroll gestures. If this parameter is set to true, you can scroll the component using your finger or mouse. If this parameter is set to false, you cannot scroll the component using your finger or mouse, but the scrolling APIs of the [Scroller](ts-container-scroll.md#scroller) are not affected.<br>Default value: **true**|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### friction<sup>11+</sup>

friction(value: number | Resource): T

Sets the friction coefficient, which takes effect when you manually scroll the scrolling area. The friction coefficient affects only the inertial scrolling process and has an indirect impact on the chain effect during inertial scrolling. If this attribute is set to a value less than or equal to 0, the default value is used.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                     |
| ------ | ---------------------------------------------------- | ---- | --------------------------------------------------------- |
| value  | number \| [Resource](ts-types.md#resource) | Yes  | Friction coefficient.<br>Default value: 0.6 for non-wearable devices and 0.9 for wearable devices.<br>From API version 11, the default value is 0.7 for non-wearable devices.<br>From API version 12, the default value is 0.75 for non-wearable devices.<br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### flingSpeedLimit<sup>11+</sup>

flingSpeedLimit(speedLimit: number): T

Sets the maximum initial velocity at the start of the fling animation that occurs after gesture-driven scrolling ends.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type  | Mandatory| Description                           |
| ---------- | ------ | ---- | ------------------------------- |
| speedLimit | number | Yes  | Maximum initial velocity at the start of the fling animation.<br>Default value: **9000**<br>Unit: vp/s<br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### fadingEdge<sup>14+</sup>

fadingEdge(enabled: Optional&lt;boolean&gt;, options?: FadingEdgeOptions): T

Sets whether to enable the edge fading effect and the length of the fading edge.

> **NOTE**
> 
> fadingEdge is implemented by setting the [overlay](ts-universal-attributes-overlay.md#overlay) and [blendMode](ts-universal-attributes-image-effect.md#blendmode11) attributes (parameter values: BlendMode.SRC_OVER and BlendApplyType.OFFSCREEN). When fadingEdge takes effect, the overlay() and blendMode() attributes of the original component are overwritten.
>
> When fadingEdge is enabled, you are advised not to set background-related attributes for the component with the fadingEdge attribute. Otherwise, the fade effect will be affected.
>
> When fadingEdge is enabled, the component with the fadingEdge attribute is clipped to the boundary. If clip is set to false for the component, the setting does not take effect.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                             | Mandatory| Description                                                        |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| enabled | Optional&lt;boolean&gt;                           | Yes  | Whether to enable the fade effect. The value true indicates that the fade effect is enabled, and the value false indicates that the fade effect is disabled.<br>Default value: **false**.|
| options | [FadingEdgeOptions](#fadingedgeoptions14) | No  | Object defining edge fading effect properties, such as the fading edge length.<br>If the value is less than 0, the default value is used. The default length is 32 vp.<br>If the value exceeds half the height of the container, it is adjusted to exactly half the height of the container.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### clipContent<sup>14+</sup>

clipContent(clip: ContentClipMode | RectShape): T

Sets the content clipping area for this scrollable component.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                             | Mandatory| Description                                                        |
| ------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| clip | [ContentClipMode](#contentclipmode14) \| [RectShape](../js-apis-arkui-shape.md#rectshape)   | Yes  | Clipping to apply, which is effective only for the content (that is, child components) of the scrollable component, not the background. When a custom rectangular area is passed through **RectShape**, only width, height, and [offset](../js-apis-arkui-shape.md#offset) relative to the component's upper left corner are supported, and rounded corners are not supported.<br></div>Default value: The default value for **Grid** and **Scroll** is **ContentClipMode.BOUNDARY**, and the default value for **List** and **WaterFlow** is **ContentClipMode.CONTENT_ONLY**.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### backToTop<sup>15+</sup>

backToTop(backToTop: boolean): T

Sets whether to enable the back-to-top feature for a scrollable component when the status bar is touched.

After receiving the status bar tap event, the scroll component on the current page can return to the top through an animation. This behavior does not affect scrollable components in background applications, which will not scroll to the top. This attribute is independent of the [enableScrollInteraction](#enablescrollinteraction11) setting.

**Atomic service API**: This API can be used in atomic services since API version 15.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                          |
| ------ | ------- | ---- | ---------------------------------------------- |
| backToTop  | boolean | Yes  | Whether to enable the back-to-top feature for a scrollable component when the status bar is touched. If this parameter is set to true, the scroll component can return to the top by tapping the status bar. If this parameter is set to false, the scroll component cannot return to the top by tapping the status bar.<br>Default value:<br>Versions earlier than API version 18: false<br>API version 18 and later: false for horizontal scrolling and true for vertical scrolling|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### scrollBarMargin<sup>20+</sup>

scrollBarMargin(margin: ScrollBarMargin): T

Sets the margin of the scroll bar. The margin is calculated based on the rounded corner distance of the scroll bar. If the scroll bar area is smaller than the minimum length of the scroll bar, the scroll bar is not displayed.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| margin  | [ScrollBarMargin](ts-types.md#scrollbarmargin20)  | Yes  |Start and end margins of the scroll bar.<br>Default value: {start: LengthMetrics.vp(0), end: LengthMetrics.vp(0)}|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### digitalCrownSensitivity<sup>18+</sup>

digitalCrownSensitivity(sensitivity: Optional\<CrownSensitivity>): T

Sets the sensitivity of the digital crown's response to events.

The component can receive the crown event (ts-universal-events-crown.md) only when it is focused. You can manage the focus by using [focusable](ts-universal-attributes-focus.md#focusable), [defaultFocus](ts-universal-attributes-focus.md#defaultfocus9) and [focusOnTouch](ts-universal-attributes-focus.md#focusontouch9).

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                                        | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| sensitivity | [Optional&lt;CrownSensitivity&gt;](ts-appendix-enums.md#crownsensitivity18) | Yes  | Sensitivity to the digital crown rotation.<br>Default value: **CrownSensitivity.MEDIUM**|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### contentStartOffset<sup>22+</sup>

contentStartOffset(offset: number | Resource): T

Sets the offset from the start of the list content. When the scroll component scrolls to the start position, the content area is offset from the boundary of the component display area by a specified distance.

If the sum of contentStartOffset and contentEndOffset exceeds the length of the content area of the scroll component, contentStartOffset and contentEndOffset are set to 0.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                           |
| ------ | ------ | ---- | ----------------------------------------------- |
| offset  | number \| [Resource](ts-types.md#resource) | Yes  | Offset from the start of the list content to the boundary of the list display area.<br>Default value: **0**<br>Unit: vp<br>If the offset is set to an abnormal value, for example, a negative number or a non-number resource, the default value is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### contentEndOffset<sup>22+</sup>

contentEndOffset(offset: number | Resource): T

Sets the offset from the end of the list content When the scroll component scrolls to the end, the content area is reserved at a specified distance from the boundary of the component display area.

If the sum of contentStartOffset and contentEndOffset exceeds the length of the content area of the scroll component, contentStartOffset and contentEndOffset are set to 0.

**Atomic service API**: This API can be used in atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                                         |
| ------ | ------ | ---- | --------------------------------------------- |
| offset  | number \| [Resource](ts-types.md#resource) | Yes  | Offset from the end of the list content to the boundary of the list display area.<br>Default value: **0**<br>Unit: vp<br>If the offset is set to an abnormal value, for example, a negative number or a non-number resource, the default value is used.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

## Events

### onReachStart<sup>11+</sup>

onReachStart(event: () => void): T

Triggered when the scrollable component reaches the start position.

This event is triggered once when the component is initialized and once when the component scrolls to the start position. If the edge effect is set to a spring effect, this event is triggered once when the swipe passes the start position, and triggered again when the swipe rebounds back to the start position.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| event  | () => void | Yes  | Called when the scroll component reaches the start position.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### onReachEnd<sup>11+</sup>

onReachEnd(event: () => void): T

Triggered when the scrollable component reaches the end position.

If the edge effect is set to a spring effect, this event is triggered once when the swipe passes the end position, and triggered again when the swipe rebounds back to the end position.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| event  | () => void | Yes  | Called when the scroll component reaches the end position.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### onScrollStart<sup>11+</sup>

onScrollStart(event: () => void): T

Triggered when the scrollable component starts scrolling initiated by the user's finger dragging the component or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](ts-container-scroll.md#scroller) starts.

Notes:

1. The scroll component starts to scroll. The input settings for triggering scrolling, such as the keyboard and mouse, are supported.

2. The scrolling animation starts after the scroll controller API is called.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| event  | () => void | Yes  | Called when the scrolling starts.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### onScrollStop<sup>11+</sup>

onScrollStop(event: () => void): T

Triggered when scrolling stops This event is called when the scrolling stops after the finger leaves the screen during the scrolling triggered by dragging the scroll component or dragging the scroll bar of the scroll component. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](ts-container-scroll.md#scroller) stops.

Notes:

1. The scrolling component stops after scrolling. You can configure the input settings for triggering scrolling, such as keyboard and mouse operations.

2. The scrolling controller API with transition animation is called, and the animation stops.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                |
| ------ | ------ | ---- | -------------------- |
| event  | () => void | Yes  | Callback upon scrolling stop.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### onWillScroll<sup>12+</sup> 

onWillScroll(handler: Optional&lt;OnWillScrollCallback&gt;): T

Triggered when the scrollable component is about to scroll.

The callback provides the amount of offset that is about to be scrolled in the current frame, along with the current scroll status and the source of the scrolling operation. The offset provided in the callback is the calculated intended scrolling offset, not the final actual scrolling offset. You can specify the intended scrolling offset for the scrollable component through the return value of this callback. The parameter type of the [onWillScroll](./ts-container-scroll.md#onwillscroll12) API of the [Scroll](./ts-container-scroll.md) component is [ScrollOnWillScrollCallback](./ts-container-scroll.md#scrollonwillscrollcallback12).

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| handler | Optional&lt;[OnWillScrollCallback](#onwillscrollcallback12)&gt; | Yes| Callback triggered when the scrollable component is about to scroll.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

> **NOTE**
> 
> onWillScroll is not triggered when ScrollEdge and ScrollToIndex without animation are called.


### onDidScroll<sup>12+</sup> 

onDidScroll(handler: OnScrollCallback): T

Triggered when the scrollable component scrolls. The return value is the offset amount by which the list has scrolled and the current scroll state.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| handler | [OnScrollCallback](#onscrollcallback12) | Yes| Callback triggered when the scrollable component scrolls.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### onScroll<sup>(deprecated)</sup>

onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): T

Triggered when the scrollable component scrolls.

This feature is supported since API version 11.

This API is deprecated since API version 12. For the **Scroll** component, the **onScroll** event is triggered before layout calculations, and you are advised to use [onWillScroll](#onwillscroll12) instead. For the **List**, Grid, and **WaterFlow** components, the **onScroll** event is triggered after layout calculations, and you are advised to use [onDidScroll](#ondidscroll12) instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| event  | (scrollOffset: number, scrollState: [ScrollState](ts-container-list.md#scrollstate)) => void| Yes| Callback triggered when the scroll component is scrolled.<br>scrollOffset: offset of each frame. If the scroll component content is scrolled up, the offset is positive. If the scroll component content is scrolled down, the offset is negative. Unit: vp<br>scrollState: current scrolling status.|

**Return value**

| Type| Description          |
| --- | -------------- |
| T | Current scrollable component.|

### onWillStartDragging<sup>21+</sup>

onWillStartDragging(handler: VoidCallback): T

Called when the scroll component starts to be dragged.

**Widget capability**: This API can be used in ArkTS widgets since API version 21.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                       | Mandatory| Description                        |
| ------- | ------------------------------------------ | ---- | ---------------------------- |
| handler | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback triggered when the scroll component starts to be dragged.|

**Return value**

| Type| Description              |
| ---- | ------------------ |
| T    | Current scrollable component.|

### onWillStopDragging<sup>20+</sup>

onWillStopDragging(handler: OnWillStopDraggingCallback): T

Called when the scroll component is released. This method is not called when the scroll component is released using the mouse wheel.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                       | Mandatory| Description                        |
| ------- | ----------------------------------------------------------- | ---- | ---------------------------- |
| handler | [OnWillStopDraggingCallback](#onwillstopdraggingcallback20) | Yes  | Callback triggered when the scroll component is released.|

**Return value**

| Type| Description              |
| ---- | ------------------ |
| T    | Current scrollable component.|

### onDidStopDragging<sup>21+</sup>

onDidStopDragging(handler: OnDidStopDraggingCallback): T

Called when the drag of the scroll component ends.

**Widget capability**: This API can be used in ArkTS widgets since API version 21.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                      | Mandatory| Description                        |
| ------- | --------------------------------------------------------- | ---- | --------------------------- |
| handler | [OnDidStopDraggingCallback](#ondidstopdraggingcallback21) | Yes  | Callback triggered when the scrolling component stops being dragged.|

**Return value**

| Type| Description              |
| ---- | ------------------ |
| T    | Current scrollable component.|

### onWillStartFling<sup>21+</sup>

onWillStartFling(handler: VoidCallback): T

Callback triggered when the scrolling component is about to start the fling effect.

**Widget capability**: This API can be used in ArkTS widgets since API version 21.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                       | Mandatory| Description                        |
| ------- | ------------------------------------------ | ---- | ---------------------------- |
| handler | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback triggered when the scrolling component is about to start the fling effect.|

**Return value**

| Type| Description              |
| ---- | ------------------ |
| T    | Current scrollable component.|

### onDidStopFling<sup>21+</sup>

onDidStopFling(handler: VoidCallback): T

Callback triggered when the fling effect of the scrolling component ends. If the fling effect is interrupted by a new swipe event, this callback is not triggered.

**Widget capability**: This API can be used in ArkTS widgets since API version 21.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                       | Mandatory| Description                        |
| ------- | ------------------------------------------ | ---- | ---------------------------- |
| handler | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback triggered when the fling effect of the scrolling component ends.|

**Return value**

| Type| Description              |
| ---- | ------------------ |
| T    | Current scrollable component.|

## ItemDragInfo

Provides information about the drag point.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name        | Type        | Read-Only| Optional|   Description        |
| ---------- | ---------- | -- | -- | ---------- |
| x | number | No| No|  X coordinate of the dragged item, in vp.   |
| y | number | No| No|  Y coordinate of the dragged item, in vp.   |

## NestedScrollOptions<sup>10+</sup>

Implements an object used to configure the [nestedScroll](#nestedscroll11) attribute.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type | Read-Only| Optional| Description             |
| ----- | ------ | ------ | -- | ----------------- |
| scrollForward | [NestedScrollMode](ts-appendix-enums.md#nestedscrollmode10) | No| No| Nested scrolling options when the scrollable component scrolls forward.|
| scrollBackward | [NestedScrollMode](ts-appendix-enums.md#nestedscrollmode10) | No| No| Nested scrolling options when the scrollable component scrolls backward.|

## EdgeEffectOptions<sup>11+</sup>

Implements an object used to configure the [edgeEffect](#edgeeffect11) attribute.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type | Read-Only| Optional| Description             |
| ----- | ------| ------- | -- | ----------------- |
| alwaysEnabled | boolean | No| No| Whether to enable the scroll effect when the component content is smaller than the component itself. The value true indicates that the sliding effect is enabled, and the value false indicates that the sliding effect is disabled.<br>**Atomic service API**: This API can be used in atomic services since API version 12.|
| effectEdge<sup>18+</sup> | number | No| Yes| Edge where the edge effect is applied.<br>With **[EffectEdge](#effectedge18).START**, the edge effect is applied to the start edge only. With **[EffectEdge](#effectedge18).END**, the edge effect is applied to the end edge only.<br>The default value is [EffectEdge](#effectedge18).START \| [EffectEdge](#effectedge18).END, which means that the edge effect is applied to both the start and end edges. If an invalid value is set, the edge effect is applied to both the start and end edges.<br>To disable the effect on both edges, set **edgeEffect** to **EdgeEffect.None**.<br>**Atomic service API**: This API can be used in atomic services since API version 18.|

## FadingEdgeOptions<sup>14+</sup>

Implements an object used to configure the [fadingEdge](#fadingedge14) attribute.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name          | Type                                                        | Read-Only| Optional| Description                                                        |
| ---------------- | ------------------------------------------------------------ | ---- | -- | ------------------------------------------------------------ |
| fadingEdgeLength | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No  | Yes| Length of the fading edge.|

## EffectEdge<sup>18+</sup>

Enumerates the edges where the edge effect is applied.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Value  | Description        |
| ----- | ---- | ------------ |
| START | 1    | Start edge.|
| END   | 2    | End edge.|

## ContentClipMode<sup>14+</sup>

Enumerates the content clipping modes for the scrollable container.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

The figure below illustrates the clipping areas corresponding to each enumeration value after the component has been configured with margin and padding attributes.

![ContentClipMode](figures/ContentClipMode.png)

| Name    |  Value | Description                                      |
| ------ | ------ | ---------------------------------------- |
| CONTENT_ONLY   |  0  | Clip to the content area, corresponding to the green area in the figure.|
| BOUNDARY |  1  | Clip to the component area, corresponding to the entire blue area in the figure.|
| SAFE_AREA  |  2  | Clip to the safe area configured for the component, corresponding to the entire yellow area in the figure.|

## OnWillScrollCallback<sup>12+</sup>

type OnWillScrollCallback = (scrollOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | ScrollResult

Callback triggered when the scrollable component is about to scroll.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| scrollOffset | number | Yes| Scroll offset of each frame. The offset is positive when the scrollable component is scrolled up and negative when it is scrolled down.<br>Unit: vp|
| scrollState | [ScrollState](ts-container-list.md#scrollstate)| Yes| Current scroll state.|
| scrollSource | [ScrollSource](ts-appendix-enums.md#scrollsource12) | Yes| Source of the current scrolling operation.|

**Return value**

| Type                         | Description                                 |
| ----------------------------- | ------------------------------------ |
| void \| [ScrollResult](#scrollresult12) |  Returns a **ScrollResult** object if the scrollable component scrolls by the offset specified by you; returns no **ScrollResult** object if the component scrolls by the offset specified by **scrollOffset** in the callback.<br>Value range: (-∞, +∞)|

## OnScrollCallback<sup>12+</sup>

type OnScrollCallback = (scrollOffset: number, scrollState: ScrollState) => void

Callback triggered when the scrollable component scrolls.

**Widget capability**: This API can be used in ArkTS widgets since API version 12.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| ------ | ------ | ------ | ------|
| scrollOffset | number | Yes| Scroll offset of each frame. The offset is positive when the scrollable component is scrolled up and negative when it is scrolled down.<br>Unit: vp|
| scrollState | [ScrollState](ts-container-list.md#scrollstate)| Yes| Current scroll state.|

## ScrollResult<sup>12+</sup>

Implements a return value object of the [OnWillScrollCallback](#onwillscrollcallback12) callback.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| ------ | ------ | ------ | -- | ------|
| offsetRemain | number | No| No| Amount by which the component is about to be scrolled, in vp.|

## ChildrenMainSize<sup>12+</sup>

Provides the size information of the child components of the **List** or **ListItemGroup** component along the main axis. This object only supports one-to-one binding to the **List** or **ListItemGroup** component.

**NOTE**
>
> - The size information in the main axis direction must be the same as the actual size of the child components in the main axis direction. If the size of the child components in the main axis direction changes or child components are added or deleted, the ChildrenMainSize object method must be used to notify the List or ListItemGroup component.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### constructor<sup>12+</sup>

constructor(childDefaultSize: number)

A constructor used to create a **ChildrenMainSize** object.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| childDefaultSize | number | Yes   | Default size of the child component along the main axis.<br>Unit: vp<br>**NOTE**<br>The value must be a finite non-negative number; otherwise, an exception will be thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.   |


### childDefaultSize<sup>12+</sup>

set childDefaultSize(value: number)

Sets the default size of the child component along the main axis.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| value | number | Yes   | Default size of the child component along the main axis.<br>Unit: vp<br>**NOTE**<br>The value must be a finite non-negative number; otherwise, an exception will be thrown.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.   |

get childDefaultSize(): number

Obtains the default size of the child component along the main axis.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| number | Default size of the child component along the main axis.<br>Unit: vp<br>Value range: [0, +∞)|

### splice<sup>12+</sup>

splice(start: number, deleteCount?: number, childrenSize?: Array\<number>): void

Performs batch operations to add, delete, or modify the size information of child components along the main axis.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| start | number | Yes   | Index starting from 0, which indicates the position at which to begin modifying the size information of child components along the main axis.<br>**NOTE**<br>1. The value must be a finite non-negative number; otherwise, an exception will be thrown.<br>2. Non-integer values are truncated to the nearest integer.<br>3. Values exceeding the maximum index do not take effect.<br>Value range: [0, +∞)|
| deleteCount | number | No   | Number of size information entries to be deleted starting from the **start** position.<br>**NOTE**<br>1.  The value must be a finite non-negative number; otherwise, it will be treated as **0**.<br>2. Non-integer values are truncated to the nearest integer.<br>3. The result of (start + deleteCount - 1) can exceed the maximum index, which will delete all size information of child components starting from the **start** position.<br>Default value: **+∞**<br>Value range: [0, +∞)|
| childrenSize | Array\<number > | No   | Size information of all child components to be inserted, starting from the **start** position.<br>Unit for each value in the array: vp<br>**NOTE**<br>1. If the values in the array are finite non-negative number, they are considered specified sizes and will not change with the default size.<br>2. If the values in the array are not finite non-negative number, they will be treated as the default size and will change with the default size.<br>The default value is an empty array.<br>Value range: [0, +∞)|


**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.   |


> **NOTE**
>
> - If only the **start** parameter is used, it means to delete the size information of the child components starting from the **start** position and beyond.
> - If only the **start** and **deleteCount** parameters are used, it means to delete the **deleteCount**-specified number of size information entries starting from the **start** position. This is generally used when you remove child components.
> - If all three parameters are used, it means to delete the **deleteCount**-specified number of size information entries starting from the **start** position, and then insert all the size information from **childrenSize** at the **start** position. This is generally used when you add child components or batch update the main axis size of child components. If it's only about adding child components, **deleteCount** should be **0**, and the number of elements in **childrenSize** should be equal to the number of child components being added. If it's only about batch updating the main axis size of child components, the number of elements in **childrenSize** should be equal to **deleteCount**, which is the number of updates being made.
> - If you want to notify that the size of a child component should be the default size, the corresponding value in **childrenSize** should not be given as a finite non-negative value, but rather as **NaN**, any negative value, or any other value that can be processed as the default size.

### update<sup>12+</sup>

update(index: number, childSize: number): void

Updates the main axis size information of the child component corresponding to the specified index.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                           | Mandatory  | Description                  |
| ---- | ----------------------------- | ---- | -------------------- |
| index | number | Yes   | Index starting from 0, which indicates the position at which to begin modifying the size information of child components along the main axis.<br>**NOTE**<br>1. The value must be a finite non-negative number; otherwise, an exception will be thrown.<br>2. Non-integer values are truncated to the nearest integer.<br>3. Values exceeding the maximum index do not take effect.<br>Value range: [0, +∞)|
| childSize | number | Yes   | Size to be updated to.<br>Unit: vp<br>**NOTE**<br>1. If the value is a finite non-negative number, it is considered a specified size and will not change with the default size.<br>2. If the value is not a finite non-negative number, it will be processed as the default size and will change with the default size.<br>Value range: [0, +∞)|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types; 3. Parameter verification failed.   |

## UIScrollableCommonEvent<sup>19+</sup>
Sets the callback for the scrolling event.
### setOnReachStart<sup>19+</sup>

setOnReachStart(callback: Callback\<void> | undefined): void

Sets the callback for the [onReachStart](./ts-container-scrollable-common.md#onreachstart11) event.

If the input parameter of an API is **undefined**, the corresponding event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void>  \| undefined | Yes  | Callback for the onReachStart event.|

### setOnReachEnd<sup>19+</sup>

setOnReachEnd(callback: Callback\<void> | undefined): void

Sets the callback for the [onReachEnd](./ts-container-scrollable-common.md#onreachend11) event.

If the input parameter is **undefined**, the event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void>  \| undefined | Yes  | Callback function of the onReachEnd event.|


### setOnScrollStart<sup>19+</sup>

setOnScrollStart(callback: Callback\<void> | undefined): void

Sets the callback for the [onScrollStart](./ts-container-scrollable-common.md#onscrollstart11) event.

If the input parameter is **undefined**, the event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void>  \|  undefined | Yes  | Callback function of the onScrollStart event.|


### setOnScrollStop<sup>19+</sup>

setOnScrollStop(callback: Callback\<void> | undefined): void

Sets the callback for the [onScrollStop](./ts-container-scrollable-common.md#onscrollstop11) event.

If the input parameter is **undefined**, the event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [Callback](./ts-types.md#callback12)\<void>  \| undefined | Yes  | Callback function of the onScrollStop event.|

### setOnScrollFrameBegin<sup>19+</sup>

setOnScrollFrameBegin(callback: OnScrollFrameBeginCallback | undefined): void

Sets the callback for the [onScrollFrameBegin](./ts-container-scroll.md#onscrollframebegin9) event.

If the input parameter is **undefined**, the event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [OnScrollFrameBeginCallback](./ts-container-scroll.md#onscrollframebegincallback18) \| undefined | Yes  | Callback function for the onScrollFrameBegin event.|


## OnWillStopDraggingCallback<sup>20+</sup>

type OnWillStopDraggingCallback = (velocity: number) => void

Called when the scroll component is released.

**Widget capability**: This API can be used in ArkTS widgets since API version 20.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory| Description                                                        |
| -------- | ------ | ---- | ------------------------------------------------------------ |
| velocity | number | Yes  | Swipe speed. The speed value is positive when the scroll component content scrolls up and negative when the scroll component content scrolls down.<br>Unit: vp/s.|

## OnDidStopDraggingCallback<sup>21+</sup>

type OnDidStopDraggingCallback = (willFling: boolean) => void

Called when the drag ends for the scroll component.

**Widget capability**: This API can be used in ArkTS widgets since API version 21.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type   | Mandatory| Description                                                                             |
| --------  | ------- | ---- | -------------------------------------------------------------------------------- |
| willFling | boolean | Yes  | Whether the fling effect is displayed after the drag ends. If true is returned, the fling effect is displayed after the drag ends. If false is returned, the fling effect is not displayed.|

## Example

### Example 1: Implementing Gesture-Based Scroll
This example configures the enableScrollInteraction attribute to enable gesture scrolling in a vertical list, with index callbacks triggered during page transitions.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](./ts-container-list.md#example-1-adding-a-scroll-event).

<!--code_no_check-->
```ts
// xxx.ets
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);

  build() {
    Column() {
      List({ space: 20, initialIndex: 0 }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .enableScrollInteraction(true)
      .listDirection(Axis.Vertical) // Arrangement direction
      .scrollBar(BarState.Off)
      .friction(0.6)
      .divider({
        strokeWidth: 2,
        color: 0xFFFFFF,
        startMargin: 20,
        endMargin: 20
      }) // Divider between rows
      .edgeEffect(EdgeEffect.Spring) // Set the edge scrolling effect to Spring.
      .onScrollIndex((firstIndex: number, lastIndex: number, centerIndex: number) => {
        console.info('first' + firstIndex);
        console.info('last' + lastIndex);
        console.info('center' + centerIndex);
      })
      .onScrollVisibleContentChange((start: VisibleListContentInfo, end: VisibleListContentInfo) => {
        console.info(' start index: ' + start.index +
          ' start item group area: ' + start.itemGroupArea +
          ' start index in group: ' + start.itemIndexInGroup);
        console.info(' end index: ' + end.index +
          ' end item group area: ' + end.itemGroupArea +
          ' end index in group: ' + end.itemIndexInGroup);
      })
      .onDidScroll((scrollOffset: number, scrollState: ScrollState) => {
        console.info(`onScroll scrollState = ScrollState` + scrollState + `, scrollOffset = ` + scrollOffset);
      })
      .width('90%')
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

![en-us_image_0000001174264378](figures/en-us_image_0000001174264378.gif)

### Example 2: Configuring Edge Fade-Out Effects
This example uses the fadingEdge attribute to enable edge fade effects for the List component and configure fade length.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](./ts-container-list.md#example-1-adding-a-scroll-event).

<!--code_no_check-->
```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
import { ListDataSource } from './ListDataSource';

@Entry
@Component
struct ListExample {
  private arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]);
  scrollerForList: Scroller = new Scroller();

  build() {
    Column() {

      List({ space: 20, initialIndex: 0, scroller: this.scrollerForList }) {
        LazyForEach(this.arr, (item: number) => {
          ListItem() {
            Text('' + item)
              .width('100%')
              .height(100)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor(0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .fadingEdge(true, { fadingEdgeLength: LengthMetrics.vp(80) })
    }
    .width('100%')
    .height('100%')
    .backgroundColor(0xDCDCDC)
    .padding({ top: 5 })
  }
}
```

![fadingEdge_list](figures/fadingEdge_list.gif)

### Example 3: Setting the Clipping Area
This example sets the clipContent attribute to change the clipping area of the content layer of the component.

<!--code_no_check-->
```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];
  @State clipContent: ContentClipMode | RectShape | undefined = undefined;

  build() {
    Column() {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width(300)
              .height(80)
              .fontSize(20)
              .textAlign(TextAlign.Center)
              .backgroundColor(Color.Grey)
          }, (item: string) => item)
        }
      }
      .backgroundColor(Color.Blue)
      .clipContent(this.clipContent)
      .scrollBar(BarState.Off)
      .friction(0.6)
      .width(300)
      .height("50%")
      .padding(10)
      .safeAreaPadding(LengthMetrics.vp(10))
      .initialOffset({ yOffset: 80 })
      .margin({ top: 20 })

      Button('clipContent SAFE_AREA')
        .onClick(() => {
          this.clipContent = ContentClipMode.SAFE_AREA;
        }).margin({ top: 30 })

      Button('clipContent BOUNDARY')
        .onClick(() => {
          this.clipContent = ContentClipMode.BOUNDARY;
        }).margin({ top: 35 })

      Button('clipContent CONTENT_ONLY')
        .onClick(() => {
          this.clipContent = ContentClipMode.CONTENT_ONLY;
        }).margin({ top: 40 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

![clipContent_scroll](figures/clipContent_scroll.gif)

### Example 4: Setting the Scrollbar Margin
This example shows how to set the scrollBarMargin attribute to adjust the scrollbar margin of the scrollable component.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](./ts-container-list.md#example-1-adding-a-scroll-event).

<!--code_no_check-->
```ts
// xxx.ets
import { ListDataSource } from './ListDataSource';
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct ListExample {
  arr: ListDataSource = new ListDataSource([0, 1, 2, 3, 4, 5, 6, 7, 8, 9]);
  @State scrollBarMargin: ScrollBarMargin = { start: LengthMetrics.vp(0), end: LengthMetrics.vp(0) };

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Column() {
        List({ space: 20, initialIndex: 0 }) {
          LazyForEach(this.arr, (item: number, index?: number) => {
            ListItem() {
              Flex({ direction: FlexDirection.Row, alignItems: ItemAlign.Center }) {
                Text('' + item)
                  .width('100%')
                  .height(80)
                  .fontSize(20)
                  .textAlign(TextAlign.Center)
                  .borderRadius(10)
                  .backgroundColor(Color.White)
                  .flexShrink(1)
              }
            }
          }, (item: number) => item.toString())
        }.width('90%')
        .friction(0.6)
        .scrollBar(BarState.On)
        .scrollBarMargin(this.scrollBarMargin)
      }.width('100%')

      Button('scrollBarMargin')
        .onClick(() => {
          this.scrollBarMargin = { start: LengthMetrics.vp(45), end: LengthMetrics.vp(70) };
        }).margin({ top: 5, left: 20 })

      Button('scrollBarMargin2')
        .onClick(() => {
          this.scrollBarMargin = { start: LengthMetrics.vp(15), end: LengthMetrics.vp(100) };
        }).margin({ top: 200, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding({ top: 5 })
  }
}
```

![scrollBarMargin_list](figures/scrollBarMargin_list.gif)
