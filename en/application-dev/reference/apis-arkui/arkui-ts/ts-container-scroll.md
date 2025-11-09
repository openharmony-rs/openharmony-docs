# Scroll

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @shengu_lancer; @yylong-->
<!--Designer: @yylong-->
<!--Tester: @liuzhenshuo-->
<!--Adviser: @HelloCrease-->

The **Scroll** component scrolls the content when the layout size of a component exceeds the size of its parent component.

>  **NOTE**
>  - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>  - If the width and height of the List component are not set when the Scroll component is nested with the List component, all content is loaded by default. In scenarios where performance is required, you are advised to specify the width and height of the List component. For details, see Lazy Loading Optimization - Lazy Loading Fails Due to Nested List in the https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-lazyforeach-optimization#section6296154115367.
>  - This component can scroll only when the size on the main axis is less than the content size.
>  - The default value of the universal attribute [clip](ts-universal-attributes-sharp-clipping.md) is **true** for the **Scroll** component.
>  - If the height of the Scroll component exceeds the screen display range, you can set the common attribute [layoutWeight](ts-universal-attributes-size.md#layoutweight) to adapt the height of the Scroll component to the remaining space of the main axis.
>  - When you touch the screen, the scrolling animation of all scrolling components within the touch range stops (except the scrolling animation triggered by the [scrollTo](#scrollto) and [scrollToIndex](#scrolltoindex) APIs), including the edge bounce animation.
>  - The component has been integrated with gesture recognition to enable touch-following functionality and other interactive features. For details about how to add custom gestures, see [Gesture Blocking Enhancement](ts-gesture-blocking-enhancement.md).

## Child Components

This component supports only one child component.
> Since API version 21, the maximum width and height of a single child component of Scroll are 16777216 px. In API version 20 and earlier versions, the maximum width and height of a single child component of Scroll are 1000000px. If the child component exceeds the size, the scrolling or display may be abnormal.


## APIs

Scroll(scroller?: Scroller)

Creates a **Scroll** component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| scroller | [Scroller](#scroller) | No| Scroller, which can be bound to scrollable components.<br>**NOTE**<br>Do not bind the scrollable component with other scrollable components, such as [ArcList](ts-container-arclist.md), [List](ts-container-list.md), [Grid](ts-container-grid.md), [Scroll](ts-container-scroll.md), and [WaterFlow](ts-container-waterflow.md).|

## Attributes

In addition to [universal attributes](ts-component-general-attributes.md) and [scrollable component common attributes](ts-container-scrollable-common.md#attributes), the following attributes are also supported.

### scrollable

scrollable(value: ScrollDirection)

Sets the scrolling direction. The scrolling offset is reset after the value is changed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                           |
| ------ | ------------------------------------------- | ---- | ----------------------------------------------- |
| value  | [ScrollDirection](#scrolldirection) | Yes  | Scrolling direction.<br>Default value: **ScrollDirection.Vertical**|

When the scrolling direction is set to [ScrollDirection.FREE](#scrolldirection), the scroll component supports only some capabilities. For details, see [Capabilities Supported in Free Scrolling Mode](#scrolldirection).

### scrollBar

scrollBar(barState: BarState)

Sets the scrollbar state. If the container component cannot be scrolled, the scrollbar is not displayed. If the size of a child component of a container component is infinite, the scrollbar cannot be dragged or scrolled with the child component.

Since API version 10, when the scrollable component has rounded corners, to prevent the scrollbar from being cut off by the corners, the scrollbar will automatically calculate the clearance distance from the top and bottom.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type                                     | Mandatory| Description                                  |
| -------- | ----------------------------------------- | ---- | -------------------------------------- |
| barState | [BarState](ts-appendix-enums.md#barstate) | Yes  | Scrollbar state.<br>Default value: **BarState.Auto**|

### scrollBarColor

scrollBarColor(color: Color | number | string)

Sets the scrollbar color.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description          |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| color  | [Color](ts-appendix-enums.md#color) \| number \| string | Yes  | Scrollbar color.<br>Default value: **'\#66182431'**.<br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**.  |

### scrollBarColor<sup>22+</sup>

scrollBarColor(color: Color | number | string | Resource)

Sets the scrollbar color.

Atomic service API: This API can be used by atomic services since API version 22.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description          |
| ------ | ------------------------------------------------------------ | ---- | -------------- |
| color  | [Color](ts-appendix-enums.md#color) \| number \| string \| [Resource](ts-types.md#resource) | Yes  | Scrollbar color.<br>Default value: **'\#66182431'**.<br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**.  |

### scrollBarWidth

scrollBarWidth(value: number | string)

Sets the scrollbar width. This attribute cannot be set in percentage. After the width is set, the scrollbar is displayed with the set width in normal state and pressed state. If the set width exceeds the height of the **Scroll** component on the main axis, the scrollbar reverts to the default width.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                      | Mandatory| Description                                     |
| ------ | -------------------------- | ---- | ----------------------------------------- |
| value  | number \| string | Yes  | Scrollbar width.<br>Default value: **4**<br>Unit: vp<br>If this parameter is set to a value less than or equal to 0, the default value is used. The value **0** means not to show the scrollbar.|

### scrollSnap<sup>10+</sup>

scrollSnap(value: ScrollSnapOptions)

Sets the scroll snapping mode.

During the snap animation, the scroll operation source type reported by the **onWillScroll** event is **ScrollSource.FLING**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                     | Mandatory| Description                      |
| ------ | ----------------------------------------- | ---- | -------------------------- |
| value  | [ScrollSnapOptions](#scrollsnapoptions10) | Yes  | Scroll snapping mode.|

### edgeEffect

edgeEffect(edgeEffect: EdgeEffect, options?: EdgeEffectOptions)

Sets the effect used when the scroll boundary is reached.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type                                             | Mandatory| Description                                                        |
| --------------------- | ------------------------------------------------- | ---- | ------------------------------------------------------------ |
| edgeEffect            | [EdgeEffect](ts-appendix-enums.md#edgeeffect)     | Yes  | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.None**|
| options<sup>11+</sup> | [EdgeEffectOptions](ts-container-scrollable-common.md#edgeeffectoptions11) | No  | Whether to enable the scroll effect when the component content is smaller than the component itself. The value **{ alwaysEnabled: true }** means to enable the scroll effect, and **{ alwaysEnabled: false }** means the opposite.<br>Default value: **{ alwaysEnabled: true }**|

### enableScrollInteraction<sup>10+</sup>

enableScrollInteraction(value: boolean)

Sets whether to support scroll gestures.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                               |
| ------ | ------- | ---- | ----------------------------------- |
| value  | boolean | Yes  | Whether to support scroll gestures. If this parameter is set to true, you can scroll the component using your finger or mouse. If this parameter is set to false, you cannot scroll the component using your finger or mouse, but the scrolling APIs of the controller [Scroller](ts-container-scroll.md#scroller) are not affected.<br>Default value: **true**|

> **NOTE**
>
> The component cannot be scrolled by dragging the mouse.

### nestedScroll<sup>10+</sup>

nestedScroll(value: NestedScrollOptions)

Sets the nested scrolling mode in the forward and backward directions to implement scrolling association with the parent component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                 | Mandatory| Description          |
| ------ | ----------------------------------------------------- | ---- | -------------- |
| value  | [NestedScrollOptions](ts-container-scrollable-common.md#nestedscrolloptions10) | Yes  | Nested scrolling options.<br>Default value: **{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }**<br>Nested scrolling does not take effect if [enablePaging](#enablepaging11) or [scrollSnap](#scrollsnap10) is set and the parent component is set to have the priority.|

### friction<sup>10+</sup>

friction(value: number | Resource)

Sets the friction coefficient, which takes effect when you manually scroll the scrolling area. The friction coefficient affects only the inertial scrolling process and has an indirect impact on the chain effect during the inertial scrolling process.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                | Mandatory| Description                                                     |
| ------ | ---------------------------------------------------- | ---- | --------------------------------------------------------- |
| value  | number \| [Resource](ts-types.md#resource) | Yes  | Friction coefficient.<br>Default value: **0.9** for wearable devices and **0.6** for non-wearable devices<br>Since API version 11, the default value for non-wearable devices is **0.7**.<br>Since API version 12, the default value for non-wearable devices is **0.75**.<br>Value range: (0, +∞).<br>If the value is less than or equal to 0, the default value is used.|

### enablePaging<sup>11+</sup>

enablePaging(value: boolean)

Sets whether to enable the swipe-to-turn-pages feature. If both **enablePaging** and **scrollSnap** are set, **scrollSnap** takes effect, but **enablePaging** does not.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| value  | boolean | Yes  | Whether to enable the swipe-to-turn-pages feature. The value **true** means to enable the swipe-to-turn-pages feature, and **false** means the opposite.<br>Default value: **false**|

### initialOffset<sup>12+</sup>

initialOffset(value: OffsetOptions)

Sets the initial scrolling offset. This attribute takes effect only during the initial layout of the component. After the initial layout, dynamically changing the value of this attribute does not have any effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| value  | [OffsetOptions](#offsetoptions12)  | Yes  |Initial scrolling offset. When the value specified is a percentage, the initial scrolling offset is calculated as the product of the **Scroll** component's size in the main axis direction and the percentage value.|

### maxZoomScale<sup>20+</sup>

maxZoomScale(scale: number)

Maximum gesture zoom ratio of the scroll component content.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| scale  | number  | Yes  |Maximum gesture zoom ratio of the scroll component content.<br>Default value: **1**.<br>Value range: (0, +∞). If the value is less than or equal to 0, the default value 1 is used.|

### minZoomScale<sup>20+</sup>

minZoomScale(scale: number)

Minimum gesture zoom ratio of the scroll component content.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| scale  | number  | Yes  |Minimum gesture zoom ratio of the scroll component content.<br>Default value: **1**.<br>Value range: (0, maxZoomScale]. If the value is less than or equal to 0, the default value 1 is used. If the value is greater than maxZoomScale, the value of maxZoomScale is used.|

>  **NOTE**
>
>  If maxZoomScale and minZoomScale are not set to 1, the scroll component enables the zoom gesture.

### zoomScale<sup>20+</sup>

zoomScale(scale: number)

Sets the zoom ratio of the scroll component content.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| scale  | number  | Yes  |Zoom ratio of the scroll component content. This parameter supports [!!](../../../ui/state-management/arkts-new-binding.md).<br>Default value: **1**.<br>Value range: (0, +∞). If the value is less than or equal to 0, the default value 1 is used.|

### enableBouncesZoom<sup>20+</sup>

enableBouncesZoom(enable: boolean)

Enables the zoom effect.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                 |
| ------ | ------- | ---- | ------------------------------------- |
| enable  | boolean  | Yes  |Enables the zoom effect. The value true indicates that the effect is enabled, and the value false indicates that the effect is disabled.<br>Default value: **true**|

## ScrollDirection

Enumerates the scrolling directions.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Value| Description                  |
| ---------- | -- | ------------------------ |
| Vertical   | 0  | Only vertical scrolling is supported.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Horizontal | 1  | Only horizontal scrolling is supported.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| Free<sup>(deprecated) </sup> | 2 | Scrolls vertically or horizontally.<br> This parameter has been deprecated since API version 9 and is not recommended since API version 20. Use FREE instead.|
| None       | 3 | Scrolling is disabled.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| FREE<sup>20+</sup>   | 4 | Free scrolling in both directions.<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

Capabilities supported in free scrolling mode:

| Supported Property| Supported Event| Supported [Scroller](#scroller) API|
| :--- | :--- | :--- |
| [scrollBar](#scrollbar) | [onWillScroll](#onwillscroll12) | [scrollTo](#scrollto) |
| [scrollBarColor](#scrollbarcolor) | [onDidScroll](#ondidscroll12) | [scrollEdge](#scrolledge) |
| [scrollBarWidth](#scrollbarwidth) | [onScrollEdge](#onscrolledge) | [scrollPage](#scrollpage9) |
| [scrollBarMargin](./ts-container-scrollable-common.md#scrollbarmargin20) | [onScrollStart](#onscrollstart9) | [currentOffset](#currentoffset) |
| [edgeEffect](#edgeeffect) | [onScrollStop](#onscrollstop9) | [scrollBy](#scrollby9) |
| [enableScrollInteraction](#enablescrollinteraction10) | - | [getItemRect](#getitemrect11) |
| [friction](#friction10) | - | - |
| [clipContent](./ts-container-scrollable-common.md#clipcontent14) | - | - |
| [initialOffset](#initialoffset12) | - | - |
| [scrollable](#scrollable) | - | - |

>  **Description:**
>  - The edgeEffect property supports only the Spring and None edge scrolling effects.
>  - The onWillScroll callback can reload the offset only in the follow-up scrolling phase.
>  - The onScrollEdge callback is triggered only once when the edge is reached and will not be triggered again after the bounce.
>  - Switching the edge mode during the flick animation does not interrupt the animation.

## ScrollSnapOptions<sup>10+</sup>

Defines a scroll snapping mode object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name      | Type   | Read Only  | Optional| Description      |
| ---------- | --------------------|-------------------- | -- | -------- |
| snapAlign  | [ScrollSnapAlign](ts-container-list.md#scrollsnapalign10)   | No| No| Alignment mode for the scroll snap position.<br>**NOTE**<br>1. Default value: **ScrollSnapAlign.NONE**|
| snapPagination | [Dimension](ts-types.md#dimension10) \| Array\<Dimension\> | No| Yes| Pagination points for scroll snapping.<br>**NOTE**<br>1. If the value is of the Dimension type, it indicates the size of each page, and the system will paginate based on this size.<br>2. If the value is of the Array\<Dimension\> type, each **Dimension** represents a pagination point, and the system will paginate accordingly. Each **Dimension** value must be within the [0, scrollable distance] range.<br>3. If this parameter is not set or **Dimension** is set to a value less than or equal to 0, the value is regarded as an invalid value. In this case, there is no scroll snapping. When the value is of the Array\<Dimension\> type, the items in the array must be monotonically increasing.<br>4. When the value is a percentage, the actual size is the product of the viewport of the **Scroll** component and the percentage value.|
| enableSnapToStart | boolean   | No| Yes| In the scroll mode of the scroll component, if this attribute is set to true, the scroll component cannot freely slide between the start and the first page. If this attribute is set to false, the scroll component can freely slide between the start and the first page.<br>**NOTE**<br>1. Default value: **true**<br>2. This attribute takes effect only when **snapPagination** is set to a value of the **Array\<Dimension\>** type; it does not work with values of the **Dimension** type.|
| enableSnapToEnd | boolean   | No| Yes| In the limited scrolling mode of the Scroll component, if this attribute is set to true, the Scroll component cannot freely slide between the last page and the end. If this attribute is set to false, the Scroll component can freely slide between the last page and the end.<br>**NOTE**<br>1. Default value: **true**<br>2. This attribute takes effect only when **snapPagination** is set to a value of the **Array\<Dimension\>** type; it does not work with values of the **Dimension** type.|

## Events

In addition to [universal events](ts-component-general-events.md) and [scrollable component common events](ts-container-scrollable-common.md#events), the following events are also supported.
>  **NOTE**
>
>  The [onWillScroll](ts-container-scrollable-common.md#onwillscroll12) and [onDidScroll](ts-container-scrollable-common.md#ondidscroll12) events are not supported.

### onScrollFrameBegin<sup>9+</sup>

onScrollFrameBegin(event: OnScrollFrameBeginCallback)

When this API is called back, the event parameter passes the scrolling amount that is about to occur. The event processing function can calculate the actual scrolling amount based on the application scenario and return the scrolling amount as the return value of the event processing function. The Scroll component scrolls according to the actual scrolling amount of the return value.

The value of **offsetRemain** can be a negative value.

If the **onScrollFrameBegin** event and **scrollBy** method are used to implement nested scrolling, set the **edgeEffect** attribute of the scrollable child component to **None**. For example, when Scroll is nested with List, set edgeEffect of List to EdgeEffect.None. Otherwise, the edge rebound animation of List will be triggered when List is scrolled, causing the nested scrolling to fail.

This event is triggered when either of the following conditions is met:

1. Scrolling is triggered by user interaction (such as finger sliding and keyboard and mouse operations).
2. The Scroll component scrolls inertia.
3. Scrolling is triggered by calling the [fling](#fling12) API.

This event is not triggered when either of the following conditions is met:

1. Scrolling control APIs other than the [fling](#fling12) API are called.
2. The out-of-bounds bounce effect is supported.
3. The scroll bar is dragged.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [OnScrollFrameBeginCallback](#onscrollframebegincallback18) | Yes  | Callback triggered when each frame scrolling starts.|

### onScroll<sup>(deprecated)</sup>

onScroll(event: (xOffset: number, yOffset: number) => void)

Triggered to return the horizontal and vertical offsets, in vp, during scrolling when the specified scroll event occurs.

Notes:

1. This event is triggered when scrolling is started by the **Scroll** component or other input settings, such as keyboard and mouse operations.

2. This event is triggered when the controller API is called.

3. This event supports the out-of-bounds bounce effect.

This API is deprecated since API version 12. You are advised to use the [onWillScroll](#onwillscroll12) event instead.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                     | Mandatory| Description                  |
| ------- | --------------------------------------------------------- | ---- | ---------------------- |
| xOffset     | number                                                  | Yes  | Horizontal offset per frame during scrolling. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp|
| yOffset     | number                                                  | Yes  | Vertical offset per frame during scrolling. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp|

### onWillScroll<sup>12+</sup>

onWillScroll(handler: ScrollOnWillScrollCallback)

Triggered before scrolling.

The callback provides the amount of offset that is about to be scrolled in the current frame, along with the current scroll status and the source of the scrolling operation. The offset provided in the callback is the calculated intended scrolling offset, not the final actual scrolling offset. You can specify the intended scrolling offset for the **Scroll** through the return value of this callback.

Notes:

1. This event is triggered when scrolling is started by the **Scroll** component or other input settings, such as keyboard and mouse operations.

2. This event is triggered when the controller API is called.

3. This event supports the out-of-bounds bounce effect.

>  **NOTE**
>
>  The callback function of the scrolling event is frequently triggered during the scrolling process. Therefore, do not perform time-consuming operations in the callback function to prevent frame freezing and frame loss. For details, see https://developer.huawei.com/consumer/cn/doc/best-practices/bpta-time-optimization-of-the-main-thread#section10112623611.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                     | Mandatory| Description                  |
| ------- | --------------------------------------------------------- | ---- | ---------------------- |
| handler | [ScrollOnWillScrollCallback](#scrollonwillscrollcallback12) | Yes  | Callback triggered before scrolling.|

### onDidScroll<sup>12+</sup>

onDidScroll(handler: ScrollOnScrollCallback)

Triggered when the **Scroll** component scrolls.

The return value is the scrolling offset amount in the current frame, along with the current scroll state.

Notes:

1. This event is triggered when scrolling is started by the **Scroll** component or other input settings, such as keyboard and mouse operations.

2. This event is triggered when the controller API is called.

3. This event supports the out-of-bounds bounce effect.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type                                                     | Mandatory| Description                  |
| ------- | --------------------------------------------------------- | ---- | ---------------------- |
| handler | [ScrollOnScrollCallback](#scrollonscrollcallback12) | Yes  | Represents the callback triggered when the **Scroll** component scrolls.|

### onScrollEdge

onScrollEdge(event: OnScrollEdgeCallback)

Triggered when scrolling reaches the edge.

Notes:

1. This event is triggered when scrolling reaches the edge after being started by the **Scroll** component or other input settings, such as keyboard and mouse operations.<br>2. This event is triggered when the controller API is called.<br>3. This event supports the out-of-bounds bounce effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [OnScrollEdgeCallback](#onscrolledgecallback18) | Yes  | Edge position to scroll to.<br>When Scroll is set to horizontal scrolling, [Edge.Center](ts-appendix-enums.md#edge) indicates the start position in the horizontal direction, and [Edge.Baseline](ts-appendix-enums.md#edge) indicates the end position in the horizontal direction. The enumerated values [Edge.Center](ts-appendix-enums.md#edge) and [Edge.Baseline](ts-appendix-enums.md#edge) have been deprecated. You are advised to use the [onReachStart](ts-container-scrollable-common.md#onreachstart11) and [onReachEnd](ts-container-scrollable-common.md#onreachend11) events to listen for whether the scroll component scrolls to the boundary.|

### onScrollEnd<sup>(deprecated) </sup>

onScrollEnd(event: () => void)

Triggered when scrolling stops.

Notes:

1. This event is triggered when scrolling is stopped by the **Scroll** component or other input settings, such as keyboard and mouse operations.<br>2. This event is triggered when the controller API is called, accompanied by a transition animation.

This event has been deprecated since API version 9 and is replaced by the [onScrollStop](#onscrollstop9) event.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | () => void | Yes  | Triggered when scrolling stops.|

### onScrollStart<sup>9+</sup>

onScrollStart(event: VoidCallback)

Triggered when scrolling starts and is initiated by the user's finger dragging the **Scroll** component or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](#scroller) starts.

Notes:

1. This event is triggered when scrolling is started by the **Scroll** component or other input settings, such as keyboard and mouse operations.<br>2. This event is triggered when the controller API is called, accompanied by a transition animation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback triggered when scrolling starts.|

### onScrollStop<sup>9+</sup>

onScrollStop(event: VoidCallback)

Triggered when scrolling stops This event is triggered when scrolling stops after the user releases the scroll or scroll bar of the Scroll component. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](#scroller) stops.

Notes:

1. This event is triggered when scrolling is stopped by the **Scroll** component or other input settings, such as keyboard and mouse operations.<br>2. This event is triggered when the controller API is called, accompanied by a transition animation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback triggered when scrolling stops.|

### onDidZoom<sup>20+</sup>

onDidZoom(event: ScrollOnDidZoomCallback)

Called when the zoom of each frame is complete.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [ScrollOnDidZoomCallback](#scrollondidzoomcallback20) | Yes  | Called when the zoom of each frame is complete.|

### onZoomStart<sup>20+</sup>

onZoomStart(event: VoidCallback)

Called when the gesture zoom starts.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback for the start of zooming.|

### onZoomStop<sup>20+</sup>

onZoomStop(event: VoidCallback)

This callback is triggered when the zooming gesture stops.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                             | Mandatory| Description              |
| ------ | --------------------------------- | ---- | ------------------ |
| event   | [VoidCallback](ts-types.md#voidcallback12) | Yes  | Callback for the end of zooming.|

## ScrollOnScrollCallback<sup>12+</sup>

type ScrollOnScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState) => void

Represents the callback triggered when the **Scroll** component scrolls.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                                   | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| xOffset     | number                                                  | Yes  | Horizontal offset per frame during scrolling. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp|
| yOffset     | number                                                  | Yes  | Vertical offset per frame during scrolling. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp|
| scrollState | [ScrollState](ts-container-list.md#scrollstate)| Yes | Current scrolling state.                                              |

>  **NOTE**
>
>  If the **onScrollFrameBegin** event and **scrollBy** method are used to implement nested scrolling, set the **edgeEffect** attribute of the scrollable child component to **None**. For example, if a **List** is nested in the **Scroll** component, **edgeEffect** of the **List** must be set to **EdgeEffect.None**.

## ScrollOnWillScrollCallback<sup>12+</sup>

type ScrollOnWillScrollCallback = (xOffset: number, yOffset: number, scrollState: ScrollState, scrollSource: ScrollSource) => void | OffsetResult

Callback triggered before scrolling.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                                   | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| xOffset     | number                                                  | Yes  | Horizontal offset per frame during scrolling. A positive offset indicates scrolling to the left, and a negative offset indicates scrolling to the right.<br>Unit: vp|
| yOffset     | number                                                  | Yes  | Vertical offset per frame during scrolling. A positive offset indicates scrolling upward, and a negative offset indicates scrolling downward.<br>Unit: vp|
| scrollState | [ScrollState](ts-container-list.md#scrollstate)| Yes | Current scrolling state.                                              |
| scrollSource | [ScrollSource](ts-appendix-enums.md#scrollsource12) | Yes| Source of the current scrolling operation.|

**Return value**

| Type                                                        | Description                                                        |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| void \| [OffsetResult](#offsetresult11) |  If OffsetResult is returned, the scrolling is performed based on the offset specified by the developer. If OffsetResult is not returned, the scrolling is performed based on the callback parameters (xOffset, yOffset).|

## OnScrollEdgeCallback<sup>18+</sup>

type OnScrollEdgeCallback = (side: Edge) => void

Represents the callback triggered when scrolling reaches an edge.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name | Type  | Mandatory| Description   |
| ------- | ----- | ---- | ------ |
| side    | [Edge](ts-appendix-enums.md#edge)  | Yes  | Edge position to scroll to.|

## OnScrollFrameBeginCallback<sup>18+</sup>

type OnScrollFrameBeginCallback = (offset: number, state: ScrollState) => OnScrollFrameBeginHandlerResult;

Represents the callback triggered before each frame scrolling starts.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                   | Mandatory| Description                      |
| ------ | ------------------------------------------------------- | ---- | -------------------------- |
| offset | number                                                  | Yes  | Amount to scroll by, in vp.|
| state  | [ScrollState](ts-container-list.md#scrollstate)| Yes  | Current scroll state.            |

**Return value**

| Type                    | Description                |
| ------------------------ | -------------------- |
| [OnScrollFrameBeginHandlerResult](#onscrollframebeginhandlerresult18)| Actual scroll offset.|

## OnScrollFrameBeginHandlerResult<sup>18+</sup>

Actual scrolling offset returned by [OnScrollFrameBeginCallback](#onscrollframebegincallback18).

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type | Read Only| Optional| Description |
| ----- | ------ | ---- | -- | ----- |
| offsetRemain<sup>9+</sup>     | number | No  | No| Actual scroll offset.<br>Unit: vp<br>**Atomic service API**: This API can be used in atomic services since API version 11.|

## ScrollOnDidZoomCallback<sup>20+</sup>

type ScrollOnDidZoomCallback = (scale: number) => void

Called when the scaling of each frame is complete.

**Atomic service API**: This API can be used in atomic services since API version 20.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name     | Type                                                   | Mandatory| Description                                                        |
| ----------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| scale     | number                                                  | Yes  | Current zoom ratio.|


## Scroller

Defines a controller for scrollable container components. It can be bound to a container component to control its scrolling behavior. A single **Scroller** instance cannot control multiple container components simultaneously. Currently, it can be bound to the following components: **ArcList**, **ArcScrollBar**, **List**, **Scroll**, **ScrollBar**, **Grid**, and **WaterFlow**.

>**NOTE**
>
>1. The binding of a **Scroller** instance to a scrollable container component occurs during the component creation phase.<br>
>2. **Scroller** APIs can only be effectively called after the **Scroller** instance is bound to a scrollable container component. Otherwise, depending on the API called, it may have no effect or throw an exception.<br>
>3. For example, with [aboutToAppear](ts-custom-component-lifecycle.md#abouttoappear), this callback is executed after a new instance of a custom component is created and before its **build()** method is called. Therefore, if a scrollable component is defined within the **build** method of a custom component, the internal scrollable component has not yet been created during the **aboutToAppear** callback of that custom component, and therefore the **Scroller** APIs cannot be called effectively.<br>
>4. For example, with [onAppear](ts-universal-events-show-hide.md#onappear), this callback is triggered after the component is mounted and displayed. Therefore, when the **onAppear** callback of a scrollable component is executed, the scrollable component has already been created and successfully bound to the **Scroller** instance, allowing the **Scroller** APIs to be called effectively.

### Objects to Import

```
scroller: Scroller = new Scroller();
```

### constructor

constructor()

A constructor used to create a **Scroller** object.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

### scrollTo

scrollTo(options: ScrollOptions)


Scrolls to the specified position.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type| Mandatory  | Description     |
| ----- | ---- | ---- | --------- |
| options | [ScrollOptions](#scrolloptions18)| Yes   | Parameters for scrolling to the specified position.

>  **NOTE**
>
> If the speed of the ScrollTo animation is greater than 200 vp/s, the components in the scrolling component area do not respond to the tap event.
>

### scrollEdge

scrollEdge(value: Edge, options?: ScrollEdgeOptions)

Scrolls to the edge of the container, regardless of the scroll axis direction. **Edge.Top** and **Edge.Start** produce the same effect, and **Edge.Bottom** and **Edge.End** produce the same effect.
By default, the **Scroll** component comes with an animation, while the **Grid**, **List**, and **WaterFlow** components do not.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type| Mandatory  | Description     |
| ----- | ---- | ---- | --------- |
| value | [Edge](ts-appendix-enums.md#edge) | Yes   | Edge position to scroll to.|
| options<sup>12+</sup>  | [ScrollEdgeOptions](#scrolledgeoptions12)| No   | Mode of scrolling to the edge position.|

### fling<sup>12+</sup>

fling(velocity: number): void


The scrolling component scrolls with inertia based on the initial speed.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type| Mandatory| Description                                                    |
| -------- | -------- | ---- | ------------------------------------------------------------ |
| velocity | number   | Yes  | Initial velocity of inertial scrolling. Unit: vp/s<br>**NOTE**<br>If the value specified is 0, it is considered as invalid, and the scrolling for this instance will not take effect. A positive value indicates scrolling towards the top, while a negative value indicates scrolling towards the bottom.<br>Value range: (-∞, +∞)|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [Scrollable Component Error Codes](../errorcode-scroll.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100004   | Controller not bound to component.                               |

### scrollPage<sup>9+</sup>

scrollPage(value:   ScrollPageOptions)

Scrolls to the next or previous page.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                          | Mandatory| Description      |
| ------ | -------------------------------------------------- | ---- | -------------- |
| value  | [ScrollPageOptions](#scrollpageoptions14) | Yes  | Page turning mode.|

### scrollPage<sup>(deprecated)</sup>

scrollPage(value: { next: boolean, direction?: Axis })

Scrolls to the next or previous page. This API is no longer maintained since API version 9. You are advised to use [scrollPage<sup>9+</sup>](#scrollpage9).

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name      | Type   | Mandatory  | Description                          |
| --------- | ------- | ---- | ------------------------------ |
| next      | boolean | Yes   | Whether to turn to the next page. The value **true** means to scroll to the next page, and **false** means to scroll to the previous page.|
| direction | [Axis](ts-appendix-enums.md#axis)    | No   | Scrolling direction: horizontal or vertical.              |

### currentOffset

currentOffset(): OffsetResult

Obtains the current scrolling offset.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type | Description|
| -------- | -------- |
|  [OffsetResult<sup>11+</sup>](#offsetresult11) | Obtains the scrolling offset.<br>**NOTE**<br>If **Scroller** is not bound to a container component or the container component is released abnormally, the return value for **currentOffset** is null.|

### scrollToIndex

scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)

Scrolls to a specified index, with support for setting an extra offset for the scroll.

When smooth animation is enabled, all items that are passed through are loaded and layout calculation is performed. If a large number of items are loaded, performance problems may occur. You are advised to call scrollToIndex without animation to jump to a position near the target, and then call scrollToIndex with animation to scroll to the target position.


>  **NOTE**
>
> 1. This method applies only to the ArcList, Grid, List, and WaterFlow components.
>
> 2. When the data source is refreshed in LazyForEach, ForEach, or Repeat, ensure that this method is called after the data is refreshed.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name               | Type| Mandatory| Description                                                    |
| --------------------- | -------- | ---- | ------------------------------------------------------------ |
| value | number   | Yes  | Index of the item to be scrolled to in the container.<br>**NOTE**<br>If the value set is a negative value or greater than the maximum index of the items in the container, the value is deemed abnormal, and no scrolling will be performed.                    |
| smooth | boolean  | No  | Whether to enable the smooth animation for scrolling to the item with the specified index. The value **true** means to enable that the smooth animation, and **false** means the opposite.<br>Default value: **false**|
| align | [ScrollAlign](#scrollalign10)  | No  | How the list item to scroll to is aligned with the container.<br>Default value when the container is **List**: **ScrollAlign.START**<br> Default value when the container is **Grid**: **ScrollAlign.AUTO**<br> Default value when the container is **WaterFlow**: **ScrollAlign.START**<br>**NOTE**<br>This parameter is only available for the **List**, **Grid**, and **WaterFlow** components.|
| options<sup>12+</sup> | [ScrollToIndexOptions](#scrolltoindexoptions12)  | No  | Options for scrolling to a specified index, for example, an extra offset for the scroll.<br>Default value: **0**, in vp|

### scrollBy<sup>9+</sup>

scrollBy(dx: Length, dy: Length)


Scrolls by the specified amount.


>  **NOTE**
>
>  This API is available for the **ArcList**, **Scroll**, **List**, **Grid**, and **WaterFlow** components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description             |
| ----- | ------ | ---- | ----------------- |
| dx |  [Length](ts-types.md#length) | Yes   | Amount to scroll by in the horizontal direction. The percentage format is not supported.<br>Value range: (-∞, +∞).|
| dy |  [Length](ts-types.md#length) | Yes   | Amount to scroll by in the vertical direction. The percentage format is not supported.<br>Value range: (-∞, +∞).|

### isAtEnd<sup>10+</sup>

isAtEnd(): boolean

Checks whether the component has scrolled to the bottom.

>  **NOTE**
>
>  This API is available for the **ArcList**, **Scroll**, **List**, **Grid**, and **WaterFlow** components.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Return value**

| Type        | Description         |
| ------- | -------- |
| boolean | The value **true** means that the component has scrolled to the bottom, and **false** means the opposite.|

### getItemRect<sup>11+</sup>

getItemRect(index: number): RectResult

Obtains the size and position of a child component relative to its container.

>  **NOTE**
>
>  This API is available for the **ArcList**, **Scroll**, **List**, **Grid**, and **WaterFlow** components.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description             |
| ----- | ------ | ---- | ----------------- |
| index | number | Yes   | Index of the target child component.|

> **NOTE**
>
> - The value of **index** must be the index of a child component visible in the display area. Otherwise, the value is considered invalid.
> - The size and position returned for an invalid value are both **0**.

**Return value**

| Type      | Description      |
| -------------------  | -------- |
| [RectResult](ts-universal-attributes-on-child-touch-test.md#rectresult) | Size and position of the child component relative to the component.<br>Unit: vp|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [Scrollable Component Error Codes](../errorcode-scroll.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100004   | Controller not bound to component.                               |
### getItemIndex<sup>14+</sup>

getItemIndex(x: number, y: number): number

Obtains the index of a child component based on coordinates.

>  **NOTE**
>
>  This API is available for the **List**, **Grid**, and **WaterFlow** components.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description             |
| ----- | ------ | ---- | ----------------- |
| x | number | Yes   | X-coordinate, in vp.|
| y | number | Yes| Y-coordinate, in vp.|

> **NOTE**
>
> The returned index is **-1** for invalid coordinates.

**Return value**

| Type      | Description      |
| -------------------  | -------- |
| number | Index of the child component.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../../errorcode-universal.md) and [Scrollable Component Error Codes](../errorcode-scroll.md).

| ID| Error Message|
| ------- | -------- |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2.Incorrect parameters types; 3. Parameter verification failed.   |
| 100004   |The controller not bound to component.                              |

## OffsetResult<sup>11+</sup>

Represents the offset values resulting from a scroll operation.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Type  | Read Only| Optional| Description                            |
| ------- |------- | ---- | ---- | -------------------------------- |
| xOffset | number |  No |  No | Horizontal scrolling offset.<br>The unit of the return value is vp.|
| yOffset | number |  No |  No | Vertical scrolling offset.<br>The unit of the return value is vp.|

## ScrollAnimationOptions<sup>12+</sup>

Provides parameters for customizing scroll animations.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type  | Read Only  | Optional| Description             |
| ----- | ------ | ------ | -- | ----------------- |
| duration | number | No| Yes| Scrolling duration.<br>Default value: **1000**<br>**NOTE**<br>A value less than 0 evaluates to the default value.|
| curve | [Curve](ts-appendix-enums.md#curve) \| [ICurve](../js-apis-curve.md#icurve9) | No| Yes| Scrolling curve.<br>Default value: **Curve.Ease**|
| canOverScroll | boolean | No| Yes| Sets whether to convert the scrolling animation to an out-of-bounds rebound animation after it scrolls to the boundary.<br>Default value: **false**<br>**NOTE**<br> Only when this attribute is set to true and edgeEffect of the component is set to [EdgeEffect.Spring] (ts-appendix-enums.md#edgeeffect), the animation scrolling to the boundary is converted to the out-of-bounds rebound animation. When this attribute is set to false: Scrolling to the boundary directly stops the animation and does not convert it to an out-of-bounds rebound animation.<br>Since API version 20, if canOverScroll in [ScrollOptions](#scrolloptions18) is set to true, the scrolling animation can stay at the boundary. After the scrolling animation crosses the boundary, it will not be converted into a rebounding animation.|

## ScrollAlign<sup>10+</sup>

Enumerates alignment modes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name    | Description                          |
| ------ | ------------------------------ |
| START   | The start edge of the list item Aligns the item header with the scrolling container header. |
| CENTER | The list item is centered along Aligns the main axis of an item to the center of the scrolling container component.       |
| END  | The end edge of the list item Aligns the tail of an item with the tail of the scrolling container component.|
| AUTO  | The list item is automatically aligned.<br>If the list item is fully contained within the display area, no adjustment is performed. Otherwise, align the head or tail of the specified item with the scrolling container component based on the principle of the shortest sliding distance so that the specified item is completely displayed in the display area.|

## ScrollToIndexOptions<sup>12+</sup>

Provides parameters for scrolling to a specific index.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type | Read Only| Optional| Description             |
| ----- | ------ | ------ | -- | ----------------- |
| extraOffset | [LengthMetrics](../js-apis-arkui-graphics.md#lengthmetrics12) | No| Yes| Extra offset for scrolling to a specified index. If the value is positive, the scrollbar is offset to the bottom. If the value is negative, the scrollbar is offset to the top.|

## ScrollPageOptions<sup>14+</sup>

Provides parameters for page scrolling behavior.

**Atomic service API**: This API can be used in atomic services since API version 14.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type| Read Only| Optional| Description                                                    |
| --------- | -------- | ---- | -- | ------------------------------------------------------------ |
| next      | boolean  | No  | No| Whether to turn to the next page. The value **true** means to scroll to the next page, and **false** means to scroll to the previous page.         |
| animation | boolean  | No  | Yes| Whether to enable the page-turning animation. The value **true** means to enable the page-turning animation, and **false** means the opposite.<br>Default value: **false**|

## OffsetOptions<sup>12+</sup>

Provides parameters for setting the initial scrolling offset.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name  | Type | Read Only| Optional| Description             |
| ----- | ------| ------- | -- | ----------------- |
| xOffset | [Dimension](ts-types.md#dimension10) | No| Yes|Horizontal scrolling offset.<br>Default value: **0**|
| yOffset | [Dimension](ts-types.md#dimension10) | No| Yes|Vertical scrolling offset.<br>Default value: **0**|

## ScrollEdgeOptions<sup>12+</sup>

Provides parameters for scrolling to the edge of a scrollable container.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type| Read Only| Optional| Description                                                  |
| --------- | -------- | ---- | -- | ------------------------------------------------------------ |
| velocity      | number  | No  | Yes| Fixed velocity for scrolling to the edge of the container. If the value specified is less than or equal to 0, the parameter will not take effect.<br>Default value: **0**<br>  Unit: vp/s         |

## ScrollOptions<sup>18+</sup>

Provides parameters for scrolling to a specific position in a scrollable container.

> **NOTE**
>
> To standardize anonymous object definitions, the element definitions here have been revised in API version 18. While historical version information is preserved for anonymous objects, there may be cases where the outer element's @since version number is higher than inner elements'. This does not affect interface usability.

**Atomic service API**: This API can be used in atomic services since API version 18.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name   | Type                                                    | Read Only| Optional| Description                                                    |
| --------- | ------------------------------------------------------------ | ---- | -- | ------------------------------------------------------------ |
| xOffset<sup>10+</sup>   | number \| string                                   | No  | No| Horizontal scrolling offset.<br>**NOTE**<br>This parameter cannot be set in percentage.<br>This parameter takes effect only when the scroll axis is the x-axis.<br>Value range: If the value is less than 0, scrolling without animation is performed and the value 0 is used. Animated scrolling stops at the starting position by default. By setting the **animation** parameter, you can enable a bounce effect when the scrolling goes beyond the boundary.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| yOffset<sup>10+</sup>   | number \| string                                   | No  | No| Vertical scrolling offset.<br>**NOTE**<br>This parameter cannot be set in percentage.<br>This parameter takes effect only when the scroll axis is the y-axis.<br>Value range: If the value is less than 0, scrolling without animation is performed and the value 0 is used. Animated scrolling stops at the starting position by default. By setting the **animation** parameter, you can enable a bounce effect when the scrolling goes beyond the boundary.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| animation<sup>10+</sup> | [ScrollAnimationOptions](#scrollanimationoptions12) \| boolean | No  | Yes| Animation configuration, which includes the following:<br>- **ScrollAnimationOptions**: custom animation settings.<br>- **boolean**: whether to enable the default spring animation.<br>Default value:<br>ScrollAnimationOptions: { duration: 1000, curve: Curve.Ease, canOverScroll: false } <br>boolean: false<br>**NOTE**<br>Currently, the **List**, **Scroll**, **Grid**, and **WaterFlow** support the **Boolean** type and **ICurve**.<br>**Atomic service API**: This API can be used in atomic services since API version 11.|
| canOverScroll<sup>20+</sup>   | boolean                                   | No  | Yes| Whether the scrolling target position can stay beyond the boundary. The scrolling can stay beyond the boundary only when edgeEffect of the component is set to EdgeEffect.Spring.<br>If this parameter is set to true, the scrolling can stay beyond the boundary. If this parameter is set to false, the scrolling cannot stay beyond the boundary.<br>Default value: **false**<br>**Atomic service API**: This API can be used in atomic services since API version 20.|

## UIScrollEvent<sup>19+</sup>
Returns the value of the [getEvent('Scroll')](../js-apis-arkui-frameNode.md#geteventscroll19) method in frameNode, which can be used to set scrolling events for the Scroll node.

UIScrollEvent is inherited from [UIScrollableCommonEvent](./ts-container-scrollable-common.md#uiscrollablecommonevent19).

### setOnWillScroll<sup>19+</sup>

setOnWillScroll(callback:  ScrollOnWillScrollCallback | undefined): void

Sets the callback for the [onWillScroll](#onwillscroll12) event.

If the input parameter is undefined, the event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [ScrollOnWillScrollCallback](./ts-container-scroll.md#scrollonwillscrollcallback12) \| undefined | Yes  | Callback function for the onWillScroll event.|

### setOnDidScroll<sup>19+</sup>

setOnDidScroll(callback: ScrollOnScrollCallback | undefined): void

Sets the callback for the [onDidScroll](#ondidscroll12) event.

If the input parameter is undefined, the event callback is reset.

**Atomic service API**: This API can be used in atomic services since API version 19.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description                      |
| ------ | ------ | ---- | -------------------------- |
| callback  | [ScrollOnScrollCallback](./ts-container-scroll.md#scrollonscrollcallback12) \| undefined | Yes  | Callback function for the onDidScroll event.|

## Example
### Example 1: Setting the Scroller
This example demonstrates the use of some attributes of the **Scroll** component and the **Scroller**.

```ts
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: number) => item.toString())
        }.width('100%')
      }
      .scrollable(ScrollDirection.Vertical) // The scrollbar scrolls in the vertical direction.
      .scrollBar(BarState.On) // The scrollbar is always displayed.
      .scrollBarColor(Color.Gray) // The scrollbar color is gray.
      .scrollBarWidth(10) // The scrollbar width is 10.
      .friction(0.6)
      .edgeEffect(EdgeEffect.None)
      .onWillScroll((xOffset: number, yOffset: number, scrollState: ScrollState) => {
        console.info(xOffset + ' ' + yOffset);
      })
      .onScrollEdge((side: Edge) => {
        console.info('To the edge');
      })
      .onScrollStop(() => {
        console.info('Scroll Stop');
      })

      Button('scroll 150')
        .height('5%')
        .onClick(() => { // Click to scroll down by 150.0 vp.
          this.scroller.scrollBy(0, 150);
        })
        .margin({ top: 10, left: 20 })
      Button('scroll 100')
        .height('5%')
        .onClick(() => { // Click to scroll down by 100.0 vp.
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({ xOffset: 0, yOffset: yOffset + 100 });
        })
        .margin({ top: 60, left: 20 })
      Button('scroll 100')
        .height('5%')
        .onClick(() => {// Click to scroll down by 100.0 vp. An animation is applied to the scrolling.
          let curve = curves.interpolatingSpring(10, 1, 228, 30); // Create a spring curve.
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({ xOffset: 0, yOffset: yOffset + 100, animation: { duration: 1000, curve: curve } });
        })
        .margin({ top: 110, left: 20 })
      Button('back top')
        .height('5%')
        .onClick(() => { // Click to go back to the top.
          this.scroller.scrollEdge(Edge.Top);
        })
        .margin({ top: 160, left: 20 })
      Button('next page')
        .height('5%')
        .onClick(() => { // Click to go to the next page.
          this.scroller.scrollPage({ next: true ,animation: true });
        })
        .margin({ top: 210, left: 20 })
      Button('fling -3000')
        .height('5%')
        .onClick(() => { // Trigger a fling with an initial velocity of -3000 vp/s.
          this.scroller.fling(-3000);
        })
        .margin({ top: 260, left: 20 })
      Button('scroll to bottom 700')
        .height('5%')
        .onClick(() => {// After the button is clicked, the component scrolls to the bottom edge at a velocity of 700 vp/s.
          this.scroller.scrollEdge(Edge.Bottom, { velocity: 700 });
        })
        .margin({ top: 310, left: 20 })
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

![en-us_image_0000001174104386](figures/scroll_scroller.gif)

### Example 2: Implementing Nested Scrolling (Method 1)
This example uses the **onScrollFrameBegin** event to achieve nested scrolling between an inner **List** component and an outer **Scroll** component.
```ts
import { LengthMetrics } from '@kit.ArkUI';

@Entry
@Component
struct NestedScroll {
  @State listPosition: number = 0; // 0 indicates scrolling to the top of the list, 1 indicates scrolling to the middle of the list, and 2 indicates scrolling to the bottom of the list.
  private arr: number[] = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
  private scrollerForScroll: Scroller = new Scroller();
  private scrollerForList: Scroller = new Scroller();

  build() {
    Flex() {
      Scroll(this.scrollerForScroll) {
        Column() {
          Text("Scroll Area")
            .width("100%")
            .height("40%")
            .backgroundColor(0X330000FF)
            .fontSize(16)
            .textAlign(TextAlign.Center)
            .onClick(() => {
              this.scrollerForList.scrollToIndex(5, false, ScrollAlign.START, { extraOffset: LengthMetrics.vp(5) });
            })

          List({ space: 20, scroller: this.scrollerForList }) {
            ForEach(this.arr, (item: number) => {
              ListItem() {
                Text("ListItem" + item)
                  .width("100%")
                  .height("100%")
                  .borderRadius(15)
                  .fontSize(16)
                  .textAlign(TextAlign.Center)
                  .backgroundColor(Color.White)
              }.width("100%").height(100)
            }, (item: string) => item)
          }
          .width("100%")
          .height("50%")
          .edgeEffect(EdgeEffect.None)
          .friction(0.6)
          .onReachStart(() => {
            this.listPosition = 0;
          })
          .onReachEnd(() => {
            this.listPosition = 2;
          })
          .onScrollFrameBegin((offset: number) => {
            if ((this.listPosition == 0 && offset <= 0) || (this.listPosition == 2 && offset >= 0)) {
              this.scrollerForScroll.scrollBy(0, offset);
              return { offsetRemain: 0 };
            }
            this.listPosition = 1;
            return { offsetRemain: offset };
          })

          Text("Scroll Area")
            .width("100%")
            .height("40%")
            .backgroundColor(0X330000FF)
            .fontSize(16)
            .textAlign(TextAlign.Center)
        }
      }
      .width("100%").height("100%")
    }.width('100%').height('100%').backgroundColor(0xDCDCDC).padding(20)
  }
}
```

![NestedScroll](figures/NestedScroll.gif)

### Example 3: Implementing Nested Scrolling (Method 2)
This example uses the **nestedScroll** attribute to achieve nested scrolling between an inner **List** component and an outer **Scroll** component.
```ts
@Entry
@Component
struct StickyNestedScroll {
  @State arr: number[] = [];

  @Styles
  listCard() {
    .backgroundColor(Color.White)
    .height(72)
    .width("100%")
    .borderRadius(12)
  }

  build() {
    Scroll() {
      Column() {
        Text("Scroll Area")
          .width("100%")
          .height("40%")
          .backgroundColor('#0080DC')
          .textAlign(TextAlign.Center)
        Tabs({ barPosition: BarPosition.Start }) {
          TabContent() {
            List({ space: 10 }) {
              ForEach(this.arr, (item: number) => {
                ListItem() {
                  Text("item" + item)
                    .fontSize(16)
                }.listCard()
              }, (item: number) => item.toString())
            }.width("100%")
            .edgeEffect(EdgeEffect.Spring)
            .nestedScroll({
              scrollForward: NestedScrollMode.PARENT_FIRST,
              scrollBackward: NestedScrollMode.SELF_FIRST
            })
          }.tabBar("Tab1")

          TabContent() {
          }.tabBar("Tab2")
        }
        .vertical(false)
        .height("100%")
      }.width("100%")
    }
    .edgeEffect(EdgeEffect.Spring)
    .friction(0.6)
    .backgroundColor('#DCDCDC')
    .scrollBar(BarState.Off)
    .width('100%')
    .height('100%')
  }

  aboutToAppear() {
    for (let i = 0; i < 30; i++) {
      this.arr.push(i);
    }
  }
}
```
![NestedScroll2](figures/NestedScroll2.gif)
### Example 4: Implementing Nested Scrolling with Parent-to-Child Scrolling Propagation
This example demonstrates how to propagate scrolling from a parent component to a child component using the **enableScrollInteraction** attribute and the **onScrollFrameBegin** event.
```ts
@Entry
@Component
struct NestedScroll {
  private headerHeight: number = 0;
  private arr: number[] = [];
  private scrollerForParent: Scroller = new Scroller();
  private scrollerForChild: Scroller = new Scroller();

  aboutToAppear(): void {
    for (let i = 0; i < 10; i++) {
      this.arr.push(i);
    }
  }

  build() {
    Scroll(this.scrollerForParent) {
      Column() {
        Text("Scroll Area")
          .width("100%")
          .height("40%")
          .backgroundColor(0X330000FF)
          .fontSize(16)
          .textAlign(TextAlign.Center)
          .onClick(() => {
            this.scrollerForChild.scrollToIndex(5);
          })
          .onSizeChange((oldValue: SizeOptions, newValue: SizeOptions) => {
            this.headerHeight = newValue.height! as number;
          })
        List({ space: 20, scroller: this.scrollerForChild }) {
          ForEach(this.arr, (item: number) => {
            ListItem() {
              Text("ListItem" + item)
                .width("100%")
                .height("100%")
                .borderRadius(15)
                .fontSize(16)
                .textAlign(TextAlign.Center)
                .backgroundColor(Color.White)
            }.width("100%").height(100)
          }, (item: number) => item.toString())
        }
        .width("100%")
        .height("100%")
        .edgeEffect(EdgeEffect.None)
        .scrollBar(BarState.Off)
        .enableScrollInteraction(false)

        Text("Scroll Area")
          .width("100%")
          .height("40%")
          .backgroundColor(0X330000FF)
          .fontSize(16)
          .textAlign(TextAlign.Center)
      }
    }
    .scrollBar(BarState.Off)
    .edgeEffect(EdgeEffect.Spring)
    .onScrollFrameBegin((offset: number, state: ScrollState) => {
      let retOffset = offset;
      let currOffset = this.scrollerForParent.currentOffset().yOffset;
      let newOffset = currOffset + offset;
      if (offset > 0) {
        if (this.scrollerForChild.isAtEnd()) {
          return { offsetRemain: offset };
        }
        if (newOffset > this.headerHeight) {
          retOffset = this.headerHeight - currOffset;
        }
        this.scrollerForChild.scrollBy(0, offset - retOffset);
      } else {
        if (this.scrollerForChild.currentOffset().yOffset <= 0) {
          return { offsetRemain: offset };
        }
        if (newOffset < this.headerHeight) {
          retOffset = this.headerHeight - currOffset;
        }
        this.scrollerForChild.scrollBy(0, offset - retOffset);
      }
      return { offsetRemain: retOffset };
    })
    .width("100%")
    .height("100%")
    .backgroundColor(0xDCDCDC)
  }
}
```
![NestedScroll3](figures/NestedScroll3.gif)
### Example 5: Setting Scroll Snapping
This example shows how to set scroll snapping for a **Scroll** component.
```ts
@Entry
@Component
struct Index {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15];
  build() {
    Scroll(this.scroller) {
      Column() {
        ForEach(this.arr, (item: number) => {
          Text(item.toString())
            .width('90%')
            .height(200)
            .backgroundColor(0xFFFFFF)
            .borderWidth(1)
            .borderColor(Color.Black)
            .borderRadius(15)
            .fontSize(16)
            .textAlign(TextAlign.Center)
        }, (item: number) => item.toString())
      }.width('100%').backgroundColor(0xDCDCDC)
    }
    .backgroundColor(Color.Yellow)
    .height('100%')
    .edgeEffect(EdgeEffect.Spring)
    .scrollSnap({snapAlign:ScrollSnapAlign.START, snapPagination:400, enableSnapToStart:true, enableSnapToEnd:true})
  }
}
```
![NestedScrollSnap](figures/NestedScrollSnap.gif)

### Example 6: Obtaining the Index of a Child Component
This example demonstrates how to obtain the index of a child component in a **List** component.

```ts
// xxx.ets
@Entry
@Component
struct ListExample {
  private arr: number[] = [];
  private scroller: ListScroller = new ListScroller();
  @State listSpace: number = 10;
  @State listChildrenSize: ChildrenMainSize = new ChildrenMainSize(100);
  @State listIndex: number = -1;
  @State itemBackgroundColorArr: boolean[] = [false];
  aboutToAppear(){
    // Initialize the data source.
    for (let i = 0; i < 10; i++) {
      this.arr.push(i);
    }
    this.listChildrenSize.splice(0, 5, [100, 100, 100, 100, 100]);
  }
  build() {
    Column() {
      List({ space: this.listSpace, initialIndex: 4, scroller: this.scroller }) {
        ForEach(this.arr, (item: number) => {
          ListItem() {
            Text('item-' + item)
              .height( item < 5 ? 100 : this.listChildrenSize.childDefaultSize)
              .width('90%')
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .borderRadius(10)
              .backgroundColor( this.itemBackgroundColorArr[item] ? 0x68B4FF: 0xFFFFFF)
          }
        }, (item: number) => item.toString())
      }
      .backgroundColor(Color.Gray)
      .layoutWeight(1)
      .scrollBar(BarState.On)
      .childrenMainSize(this.listChildrenSize)
      .alignListItem(ListItemAlign.Center)
      .gesture(
        PanGesture()
          .onActionUpdate((event: GestureEvent) => {
            if (event.fingerList[0] != undefined && event.fingerList[0].localX != undefined && event.fingerList[0].localY != undefined) {
              this.listIndex = this.scroller.getItemIndex(event.fingerList[0].localX, event.fingerList[0].localY);
              this.itemBackgroundColorArr[this.listIndex] = true;
            }
          })
      )
      .gesture(
        TapGesture({ count: 1 })
          .onAction((event: GestureEvent) => {
            if (event) {
              this.itemBackgroundColorArr.splice(0,this.itemBackgroundColorArr.length);
            }
          })
      )

      Text('You are currently at index '+ this.listIndex)
        .fontColor(Color.Red)
        .height(50)
    }
  }
}
```

![ScrollEdgeAtVelocity](figures/getItemIndex_list.gif)

### Example 7: Setting Edge Fading
This example demonstrates how to implement a **Scroll** component with an edge fading effect and set the length of the fading edge.

```ts
// xxx.ets
import { LengthMetrics } from '@kit.ArkUI';
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: string) => item)
        }.width('100%')
      }
      .fadingEdge(true,{fadingEdgeLength:LengthMetrics.vp(80)})



    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

![fadingEdge_scroll](figures/fadingEdge_scroll.gif)

### Example 8: Setting the Single-Side Edge Effect

This example demonstrates how to set a single-side edge effect for the **Scroll** component using the **edgeEffect** API.

```ts
// xxx.ets
@Entry
@Component
struct ScrollExample {
  scroller: Scroller = new Scroller();
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12];

  build() {
    Stack({ alignContent: Alignment.TopStart }) {
      Scroll(this.scroller) {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('90%')
              .height(150)
              .backgroundColor(0xFFFFFF)
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .margin({ top: 10 })
          }, (item: string) => item)
        }.width('100%')
      }
      .edgeEffect(EdgeEffect.Spring,{alwaysEnabled:true,effectEdge:EffectEdge.START})
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

![edgeEffect_scroll](figures/edgeEffect_scroll.gif)

### Example 9 (Swipe Page Turning Effect)

This example implements the swipe page turning effect of the Scroll component using the enablePaging API.

```ts
// xxx.ets
@Entry
@Component
struct EnablePagingExample {
  private arr: number[] = [0, 1, 2, 3, 4, 5, 6, 7, 8, 9]

  build() {
    Stack({ alignContent: Alignment.Center }) {
      Scroll() {
        Column() {
          ForEach(this.arr, (item: number) => {
            Text(item.toString())
              .width('100%')
              .height('100%')
              .borderRadius(15)
              .fontSize(16)
              .textAlign(TextAlign.Center)
              .backgroundColor(0xFFFFFF)
          }, (item: number) => item.toString())
        }
      }.width('90%').height('90%')
      .enablePaging(true)
    }.width('100%').height('100%').backgroundColor(0xDCDCDC)
  }
}
```

![enablePaging](figures/enablePaging.gif)

### Example 10 (Setting the Overflow Stay Effect)

This example uses the scrollTo API to implement the overflow stay effect of the Scroll component.

```ts
// xxx.ets
import { curves } from '@kit.ArkUI';

@Entry
@Component
struct StickyNestedScroll {
  scroller: Scroller = new Scroller;

  build() {
    Column() {
      Row() {
        Button('scrollTo with animation').onClick(() => {
          let curve = curves.interpolatingSpring(0.5, 5, 10, 15) // Create a spring curve.
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({
            xOffset: 0,
            yOffset: yOffset - 100,
            animation: { duration: 1000, curve: curve, canOverScroll: true },
            canOverScroll: true
          })
        }).margin({ top: 10 })
        Button('scrollTo without animation').onClick(() => {
          const yOffset: number = this.scroller.currentOffset().yOffset;
          this.scroller.scrollTo({
            xOffset: 0,
            yOffset: yOffset - 100,
            animation: false,
            canOverScroll: true
          })
        }).margin({ top: 10, left: 20 })
      }.margin({ bottom: 20 })

      Scroll(this.scroller) {
        Column() {
          Text('Scroll Area')
            .width('100%')
            .height('100%')
            .backgroundColor('#0080DC')
            .textAlign(TextAlign.Center)
        }
        .width('100%')
        .height('100%')
      }
      .scrollable(ScrollDirection.Vertical)
      .edgeEffect(EdgeEffect.Spring) // Set the edge effect.
      .fadingEdge(false) // Disable the edge fade effect.
      .scrollBar(BarState.Auto)
      .friction(undefined)
      .backgroundColor('#DCDCDC')
      .width('100%')
      .height('50%')
    }
  }
}
```




### Example 11 (Free scrolling and zooming)

This example implements the free scrolling and zooming effects of the Scroll component.
```ts
@Entry
@Component
struct ScrollZoomExample {
  @State currScale:number = 1;
  build() {
    Column() {
      Scroll() {
        Image($r('app.media.image1')) // 'app.media.image1' (Replace it with the actual image.)
      }
      .height(400)
      .scrollable(ScrollDirection.FREE)
      .minZoomScale(1)
      .maxZoomScale(2)
      .zoomScale(this.currScale!!)
      .enableBouncesZoom(true)
      .onDidZoom((scale: number) => {
        console.info(`onDidZoom:${scale}`);
      })
      .onZoomStart(() => {
        console.info('onZoomStart');
      })
      .onZoomStop(() => {
        console.info('onZoomStop');
      })
    }.width('100%').height('100%')
  }
}
```
![free_scroll_zoom](figures/free_scroll_zoom.gif)
