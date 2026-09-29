# Scroller

```TypeScript
declare class Scroller
```

Defines a controller for scrollable container components. It can be bound to a container component to control its scrolling behavior. A single **Scroller** instance cannot control multiple container components simultaneously. Currently, it can be bound to the following components: **ArcList**, **ArcScrollBar**, **List**, **Scroll**, **ScrollBar**, **Grid**, and **WaterFlow**.

> **NOTE:** 
> 
> 1. The binding between the **Scroller** controller and the scroll container component occurs during component creation.

> 2. The **Scroller** methods can be called normally only after the **Scroller** controller is bound to the scroll container component. Otherwise, depending on the API called, the call may not take effect or may throw an exception.

> 3. Take [aboutToAppear](arkts-arkui-common-comp-basecustomcomponent-c.md#abouttoappear) as an example. **aboutToAppear** is executed after a new instance of the custom component is created and before its
> **build()** method is executed. Therefore, if the scroll component is inside the **build()** of a custom component,
> the internal scroll component has not been created yet when **aboutToAppear** of the custom component is executed,
> and the **Scroller** methods cannot be called normally.

> 4. Take [onAppear](arkts-arkui-common-comp-commonmethod-c.md#onappear) as an example. This callback is triggered after the component is mounted and displayed. Therefore, when the **onAppear** callback of the scroll component is executed, the scroll component has been created and successfully bound to the **Scroller**, and the **Scroller** methods can be called normally.

**Since:** 7

<!--Device-unnamed-declare class Scroller--><!--Device-unnamed-declare class Scroller-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## constructor

```TypeScript
constructor()
```

A constructor used to create a **Scroller** object.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-constructor()--><!--Device-Scroller-constructor()-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## contentSize

```TypeScript
contentSize(): SizeResult
```

Obtains the content size.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-Scroller-contentSize(): SizeResult--><!--Device-Scroller-contentSize(): SizeResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [SizeResult](arkts-arkui-common-comp-sizeresult-i.md) | Total size of the scrollable component's content, including the content width and height.<br>Unit: vp |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## currentOffset

```TypeScript
currentOffset() : OffsetResult
```

Obtains the current scroll offset.

> **NOTE:** 
> 
> 1. When the **Scroller** is not bound to a component, this API returns **undefined**, which is not declared in the API. It is recommended to use the [offset](#offset) function, whose return type explicitly includes **undefined**.
> 
> 2. The **Grid**, **List**, and **WaterFlow** components have a lazy loading mechanism. When the component content has not been loaded and laid out, the total content offset is obtained through estimation, and the estimation result may contain errors. For the **List** component, the [childrenMainSize](arkts-arkui-list-comp-attribute.md#childrenmainsize) attribute can be used to resolve the inaccurate estimation. For **Grid** and **WaterFlow**, there is currently no solution for the inaccurate estimation.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-currentOffset() : OffsetResult--><!--Device-Scroller-currentOffset() : OffsetResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [OffsetResult](arkts-arkui-scroll-comp-offsetresult-i.md) | Current total scroll offset. **xOffset** indicates the total horizontal scroll offset, and **yOffset** indicates the total vertical scroll offset.<br><br>**Since:** 11 |

## fling

```TypeScript
fling(velocity: number): void
```

The scroll component performs inertial scrolling based on the initial velocity passed in. This API can be used to simulate a fling effect.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Scroller-fling(velocity: number): void--><!--Device-Scroller-fling(velocity: number): void-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| velocity | number | Yes | Initial velocity of the inertial scroll. Unit: vp/s<br>**Note:** <br>If **velocity** is set to **0**, the current scroll does not take effect and no scroll animation is generated. If the value is positive, the component scrolls toward the top; if the value is negative, the component scrolls toward the bottom. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## getFrameNode

```TypeScript
getFrameNode(): FrameNode | undefined
```

Obtains the FrameNode corresponding to this scroller.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-Scroller-getFrameNode(): FrameNode | undefined--><!--Device-Scroller-getFrameNode(): FrameNode | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| FrameNode &#124; undefined | Returns the FrameNode bound to this scroller. If the scroller is not bound to a component, the return value is undefined. |

## getItemIndex

```TypeScript
getItemIndex(x: number, y: number): number
```

Obtains the index of a child component based on coordinates.

> **NOTE:** 
> 
> This API is available for the **List**, **Grid**, and **WaterFlow** components.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-Scroller-getItemIndex(x: number, y: number): number--><!--Device-Scroller-getItemIndex(x: number, y: number): number-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| x | number | Yes | X-coordinate, in vp. |
| y | number | Yes | Y-coordinate, in vp. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the child component hit by the coordinates. If the coordinates do not hit any child component, **-1** is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## getItemRect

```TypeScript
getItemRect(index: number): RectResult
```

Obtains the size and position of a child component relative to its container.

> **NOTE:** 
> 
> This API is available for the **ArcList**, **Scroll**, **List**, **Grid**, and **WaterFlow** components.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-Scroller-getItemRect(index: number): RectResult--><!--Device-Scroller-getItemRect(index: number): RectResult-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | number | Yes | Index of the target child component. |

**Return value:**

| Type | Description |
| --- | --- |
| [RectResult](arkts-arkui-common-comp-rectresult-i.md) | Size and position of the child component relative to the component.<br>Unit: vp |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:<br> 1. Mandatory parameters are left unspecified. <br> 2. Incorrect parameters types. <br> 3. Parameter verification failed. |
| [100004](../errorcode-router.md#100004-incorrect-route-name) | Controller not bound to a component. |

## isAtEnd

```TypeScript
isAtEnd(): boolean
```

Checks whether the component has scrolled to the bottom.

> **NOTE:** 
> 
> This API is available for the **ArcList**, **Scroll**, **List**, **Grid**, and **WaterFlow** components.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-isAtEnd(): boolean--><!--Device-Scroller-isAtEnd(): boolean-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| boolean | The value **true** means that the component has scrolled to the bottom, and **false** means the opposite. |

## offset

```TypeScript
offset() : OffsetResult | undefined
```

Obtains the current scroll offset. Except for **undefined** in the API declaration, other information is the same as that of the [currentOffset](#currentoffset) API.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-Scroller-offset() : OffsetResult | undefined--><!--Device-Scroller-offset() : OffsetResult | undefined-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Return value:**

| Type | Description |
| --- | --- |
| [OffsetResult](arkts-arkui-scroll-comp-offsetresult-i.md) &#124; undefined | Current total scroll offset. **xOffset** indicates the total horizontal scroll offset, and **yOffset** indicates the total vertical scroll offset. If the **Scroller** is not bound to a component, this API returns **undefined**. |

## scrollBy

```TypeScript
scrollBy(dx: Length, dy: Length)
```

Scrolls by the specified amount.

> **NOTE:** 
> 
> - This API is available for the **ArcList**, **Scroll**, **List**, **Grid**, and **WaterFlow** components.
> 
> - Component behavior varies:
> 
> - The [ArcList](arkts-arkui-arclist-comp.md) and [List](arkts-arkui-list-comp.md) components load and lay out all items that are passed through.
> 
> - The **Grid** components and the **WaterFlow** components in [SLIDING_WINDOW](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) mode directly estimate the items to be displayed when the jump distance is large (greater than twice the component main axis height). A jump refers to a one-frame scroll.
> 
> - The **WaterFlow** components in [ALWAYS_TOP_DOWN](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) mode load and lay out all items passed through when jumping backward (when **dx** or **dy** is positive), and jump directly to the corresponding position when jumping forward (when **dx** or **dy** is negative). A jump refers to a one-frame scroll.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-scrollBy(dx: Length, dy: Length)--><!--Device-Scroller-scrollBy(dx: Length, dy: Length)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| dx | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Amount to scroll by in the horizontal direction. The percentage format is not supported.<br>Value range: (-∞, +∞). |
| dy | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Amount to scroll by in the vertical direction. The percentage format is not supported.<br>Value range: (-∞, +∞). |

## scrollEdge

```TypeScript
scrollEdge(value: Edge, options?: ScrollEdgeOptions)
```

Scrolls to the edge of the container, regardless of the scroll axis direction. **Edge.Top** and **Edge.Start** behave the same, and **Edge.Bottom** and **Edge.End** behave the same. This API can be used for scenarios such as returning to the top and jumping to the end of the content.

By default, the **Scroll** component comes with an animation, while the **Grid**, **List**, and **WaterFlow** components do not.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions)--><!--Device-Scroller-scrollEdge(value: Edge, options?: ScrollEdgeOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Edge](../arkts-apis/arkts-arkui-edge-e.md) | Yes | Edge position to scroll to. |
| options | [ScrollEdgeOptions](arkts-arkui-scroll-comp-scrolledgeoptions-i.md) | No | Mode of scrolling to the edge position.<br>&lt;em&gt;Atomic service API&lt;/em&gt;: This API can be used in atomic services since API version 12.<br>**Since:** 12 |

## scrollPage

```TypeScript
scrollPage(value: ScrollPageOptions)
```

Scrolls to the next or previous page.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-scrollPage(value: ScrollPageOptions)--><!--Device-Scroller-scrollPage(value: ScrollPageOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScrollPageOptions](arkts-arkui-scroll-comp-scrollpageoptions-i.md) | Yes | Paging mode. It contains the **next** (whether to page down) and **animation** (whether to enable the paging animation) fields, which are used to specify the paging behavior.<br>**Since:** 14 |

<a id="scrollpage-1"></a>

## scrollPage

```TypeScript
scrollPage(value: { next: boolean; direction?: Axis })
```

Scrolls to the next or previous page.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [scrollPage](#scrollpage)

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-Scroller-scrollPage(value: { next: boolean; direction?: Axis })--><!--Device-Scroller-scrollPage(value: { next: boolean; direction?: Axis })-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | { next: boolean; direction?: Axis } | Yes | next: Whether to turn to the next page. The value &lt;em&gt;true&lt;/em&gt; means to scroll to the next page, and &lt;em&gt;false&lt;/em&gt; means to scroll to the previous page. direction: Scrolling direction: horizontal or vertical. |

## scrollTo

```TypeScript
scrollTo(options: ScrollOptions)
```

Scrolls to a specified position. This API can be used for scenarios such as directory navigation, returning to the top, and locating search results.

> **NOTE:** 
> 
> - If the scrolling speed of the **scrollTo** animation exceeds 200 vp/s, the components within the scrollable area will not respond to click events.
> 
> - Component behavior varies:
> 
> - The [ArcList](arkts-arkui-arclist-comp.md) and [List](arkts-arkui-list-comp.md) components load and lay out all items that are passed through.
> 
> - The **Grid** components and the [WaterFlow](arkts-arkui-waterflow-comp.md) components in [SLIDING_WINDOW](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) mode directly estimate the items to be displayed when the jump distance is large (greater than twice the component main axis height). A jump refers to a one-frame scroll.
> 
> - The **WaterFlow** components in [ALWAYS_TOP_DOWN](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) mode load and lay out all items passed through when jumping backward (when **dx** or **dy** is positive), and jump directly to the corresponding position when jumping forward (when **dx** or **dy** is negative). A jump refers to a one-frame scroll.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-scrollTo(options: ScrollOptions)--><!--Device-Scroller-scrollTo(options: ScrollOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ScrollOptions](arkts-arkui-scroll-comp-scrolloptions-i.md) | Yes | Parameters for scrolling to a specified position, including fields such as **xOffset**, **yOffset**, **animation**, and **canOverScroll**, used to specify the scroll target position and scroll behavior.<br>**Since:** 18 |

## scrollToIndex

```TypeScript
scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)
```

Scrolls to a specified index, with support for setting an extra offset for the scroll.

When the smooth animation is enabled, all items passed through are loaded and laid out. Loading a large number of items may cause performance issues. To optimize performance, you should first call **scrollToIndex** without animation to jump to a position near the target, and then call **scrollToIndex** with animation to scroll to the target position.

> **NOTE:** 
> 
> 1. This API is supported only by the **ArcList**, **Grid**, **List**, and **WaterFlow** components.
> 
> 2. When refreshing the data source in [LazyForEach](arkts-arkui-lazyforeach-comp.md), [ForEach](arkts-arkui-foreach-comp-attribute.md#foreachattribute), or [Repeat](arkts-arkui-repeat-comp.md), ensure that this API is called after the data refresh is complete.
> 
> 3. Since API version 11, [contentStartOffset](arkts-arkui-list-comp-attribute.md#contentstartoffset) and [contentEndOffset](arkts-arkui-list-comp-attribute.md#contentendoffset) are supported in **List**. Since API version 22,contentStartOffsetand contentEndOffsetcan be set in the **Grid** and **WaterFlow** components.
> 
> - When **contentStartOffset** is set for the scroll container component and **ScrollAlign** is set to **START**,the head of the specified item is aligned with the **contentStartOffset** position of the scroll container component when scrolling ends.
> 
> - When **contentEndOffset** is set for the scroll container component and **ScrollAlign** is set to **END**, the tail of the specified item is aligned with the **contentEndOffset** position of the scroll container component when scrolling ends.
> 
> - When **contentStartOffset** or **contentEndOffset** is set for the scroll container component and
> **ScrollAlign** is set to **AUTO**, no adjustment is made if the specified item is completely within the display
> area. Otherwise, based on the principle of the shortest scrolling distance, the head of the specified item is
> aligned with the **contentStartOffset** position of the scroll component, or the tail of the specified item is
> aligned with the **contentEndOffset** position of the scroll component, so that the specified item is fully
> displayed.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-Scroller-scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)--><!--Device-Scroller-scrollToIndex(value: number, smooth?: boolean, align?: ScrollAlign, options?: ScrollToIndexOptions)-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Index of the item to be scrolled to in the container.<br>**NOTE:** <br>If the value set is a negative value or greater than the maximum index of the items in the container, the value is deemed abnormal, and no scrolling will be performed. |
| smooth | boolean | No | Whether to animate scrolling to the index of a list item. The value **true** indicates that animation is used, and **false** indicates that no animation is used. When not passed, no animation is used by default.<br>Default value: **false**.<br>**Since:** 12 |
| align | [ScrollAlign](arkts-arkui-scroll-comp-scrollalign-e.md) | No | Alignment between the element to scroll to and the current container. You can select the corresponding alignment based on whether the item is expected to be displayed at the start, end, or center.<br>Default value: **ScrollAlign.START** for **List**, **ScrollAlign.AUTO** for **Grid**, and **ScrollAlign.START** for **WaterFlow**.<br>**NOTE:** <br>This parameter is supported only by the **List**, **Grid**, and **WaterFlow** components.<br>**Since:** 12 |
| options | [ScrollToIndexOptions](arkts-arkui-scroll-comp-scrolltoindexoptions-i.md) | No | Options for scrolling to the specified index, including the **extraOffset** field, which specifies the extra offset after scrolling.<br>When not passed, there is no extra offset.<br><br>**Since:** 12 |
