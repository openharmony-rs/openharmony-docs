# Swiper properties/events

In addition to the universal attributes, the following attributes are supported.

In addition to the universal events, the following events are supported.

**Inheritance/Implementation:** SwiperAttribute extends CommonMethod<SwiperAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## autoPlay

```TypeScript
autoPlay(value: boolean)
```

Sets whether to enable automatic playback for child components, with the direction from the smallest to largest index.

If [loop](#loop) is set to **false**, the automatic playback stops at the last page and resumes after navigated away from the last page using gestures. If the **Swiper** component becomes invisible, the playback stops.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable automatic playback for child components.<br>**true**: yes; **false**: no<br>If an invalid value is passed, the value **false** is used. |

## autoPlay

```TypeScript
autoPlay(autoPlay: boolean, options: AutoPlayOptions)
```

Sets whether to enable automatic playback for child components, with **options** controlling whether child components stop automatic playback when the screen is pressed by fingers, a mouse device, or other input devices.

If [loop](#loop) is set to **false**, automatic playback stops at the last page and resumes after navigated away from the last page using gestures. Automatic playback also stops when the **Swiper** component is not visible.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| autoPlay | boolean | Yes | Whether to enable automatic playback for child components.<br>**true**: yes; **false**: no<br>If an invalid value is passed, the value **false** is used. |
| options | [AutoPlayOptions](arkts-arkui-autoplayoptions-i.md) | Yes | Whether child components stop automatic playback when the screen is pressed by fingers, a mouse device, or other input devices. If **stopWhenTouched** is set to **true**, automatic playback resumes after any finger lifts in multi-touch scenarios.<br>Default value: **{ stopWhenTouched: true }**. |

## cachedCount

```TypeScript
cachedCount(value: number)
```

Sets the number of child components to be preloaded (cached), which are needed for the specific number of pages immediately before and after the current page. If a preceding item is deleted, the succeeding items will shift forward. For example, if **cachedCount** is set to **1**, the child components on the previous page and the next page are cached. If **swipeByGroup** in **displayCount** is set to **true**, child components are cached by group. For example, if **cachedCount** is set to **1** and **swipeByGroup** is set to **true**, the child components in the previous and next groups are cached.

> **NOTE:** 
> 
> - In continuous scrolling scenarios where one **Swiper** child component is displayed per screen, setting
> **cachedCount** to **1** or **2** is typically sufficient. For best practices, see
> [Optimizing Frame Loss During Swiper Component Loading — Caching Data Items](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-swiper_high_performance_development_guide#section143504547145).
> 
> 
> - This parameter takes effect only when used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or the [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) component that has virtualScroll enabled. Child components outside the visible area and cache range will be released after this parameter takes effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of child components to be preloaded (cached).<br>Default value: **1**<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

## cachedCount

```TypeScript
cachedCount(count: number, isShown: boolean)
```

Sets the number of child components to be cached.

> **NOTE:** 
> 
> - When the value of **isShown** is **true** and the value of **count** is too large, if there are insufficient loadable nodes within the preload range, the same loadable node will only be laid out on one side in loop scenarios.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of child components to be preloaded (cached).<br>Default value: **1**<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |
| isShown | boolean | Yes | Whether the cached nodes within the range rendered without being added to the render tree.<br>**true**: yes; **false**: no<br>If an invalid value is passed, the value **false** is used. |

## cachedCount

```TypeScript
cachedCount(count: number, options: CachedCountOptions)
```

Sets the number of child components to be prloaded and configuration options.

> **NOTE:** 
> 
> - When **independent** in options is set to **true**, the number of preloaded child components is calculated based on the value of **count**, which is decoupled from the **swipeByGroup** calculation of [displayCount](#displaycount-1).For example, if the value of **count** in **cachedCount** is **1**, the previous and next child components of the current child node are preloaded.
> 
> - If **swipeByGroup** of **displayCount** is set to **true** and **independent** of **options** is set to
> **false** (default value), the number of child components to be preloaded is calculated by group. For example, if
> **count** of **cachedCount** is **1**, **value** of **displayCount** is **2**, and **swipeByGroup** of
> **displayCount** is **true**, two child components of the previous group and two child components of the next
> group of the current group are preloaded.
> 
> - This parameter takes effect only when used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or the [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) component that has virtualScroll enabled. Child components outside the cache range will be released after this parameter takes effect.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 24.

**Widget capability:** This API can be used in ArkTS widgets since API version 24.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of child components to be preloaded (cached).<br>The value range is [0, +∞). If the value is less than 0, the value **1** is used. |
| options | [CachedCountOptions](arkts-arkui-cachedcountoptions-i.md) | Yes | Configuration options for child components to be preloaded. |

## curve

```TypeScript
curve(value: Curve | string | ICurve)
```

Sets the animation curve. The interpolating spring curve is used by default. For details about common curves, see Curve. You can also create custom curves (interpolation curve objects) by using the API provided by the [interpolation calculation](../arkts-apis/arkts-arkui-curves.md) module.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Curve &#124; string &#124; ICurve | Yes | Animation curve.<br>The **string** type is deprecated since API version 9 (see [curves.init](../arkts-apis/arkts-arkui-curves-init-f.md), [curves.steps](../arkts-apis/arkts-arkui-curves-steps-f.md), [curves.cubicBezier](../arkts-apis/arkts-arkui-curves-cubicbezier-f.md), and [curves.spring](../arkts-apis/arkts-arkui-curves-spring-f.md)). Use **Curve** or **ICurve** instead.<br>Default value: **[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md)(-1, 1, 328, 34)**.<br>**Since:** 10 |

## customContentTransition

```TypeScript
customContentTransition(transition: SwiperContentAnimatedTransition)
```

Defines a custom page transition animation. During finger-following swipes and post-release transition animations, this triggers a frame-by-frame callback for all pages in the viewport, allowing you to customize animations by modifying properties like opacity, scale, and translation.

Instructions:

1. This API does not work when **prevMargin** and **nextMargin** are set in such a way that the **Swiper**
frontend and backend display the same page during loop playback.
2. During finger-following swipes and post-release transition animations,
the [SwiperContentTransitionProxy](arkts-arkui-swipercontenttransitionproxy-i.md) callback is invoked for all pages in the viewport on a frame-by-frame basis. For example, when there are two pages whose subscripts are 0 and 1 in the viewport, two callbacks whose indexes are 0 and 1 are invoked in each frame.
3. When the **swipeByGroup** parameter of the **displayCount** attribute is set to **true**,
the callback is invoked for all pages in a group if any page in the group is within the viewport; and all pages in a group are removed from the render tree if none of them are within the viewport.
4. During finger-following swipes and post-release transition animations, the default animation (page scrolling)
is still effective. If you do not want the page to scroll, you can set the **translate** property on the main axis to offset the page scrolling. For example, if the value of **displayCount** is **2** and there are two pages whose subscripts are 0 and 1 within the viewport, you can set the **translate** property on the main axis to the following on a frame-by-frame basis: **translate** for page 0 = **-position** x **mainAxisLength**; **translate** for page 1 = **-(position - 1)** x **mainAxisLength**

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [SwiperContentAnimatedTransition](arkts-arkui-swipercontentanimatedtransition-i.md) | Yes | Information about the custom page transition animation. |

## disableSwipe

```TypeScript
disableSwipe(value: boolean)
```

Sets whether to disable the swipe feature.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to disable the swipe feature. The value **true** means to disable the feature, and **false** means the opposite.<br>Default value: **false**. |

## displayArrow

```TypeScript
displayArrow(value: ArrowStyle | boolean, isHoverShow?: boolean)
```

Sets the arrow style of the navigation indicator.

> **NOTE:** 
> 
> When all child nodes fit within the viewport, resulting in only one screen's worth of content being visible, the
> **Swiper** component displays only that screen without any left or right page-turning arrows.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ArrowStyle](arkts-arkui-arrowstyle-i.md) &#124; boolean | Yes | Arrow and background to set. In cases of exceptions, the default values in the **ArrowStyle** object are used. The value **true** means to show the arrow and background in the default styles, and **false** means to hide the arrow and background.<br>Default value: **false**. |
| isHoverShow | boolean | No | Whether to show the arrow on mouse hover.<br>Default value: **false**.<br>**NOTE:** <br>1. **false**: The arrow is always displayed.<br>2. **true**: The arrow is displayed.<br>With navigation indicators, the arrow is displayed when the mouse pointer hovers over the indicators or arrow areas.<br>Without navigation indicators, the arrow is displayed when the mouse pointer hovers over the **Swiper** display area.<br>3. When the arrow is displayed, clicking the arrow turns pages. |

## displayCount

```TypeScript
displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean)
```

Sets the number of elements to display per page.

**number** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The child elements are stretched or shrunk to equally divide the **Swiper** component's width (minus **displayCount-1** times **itemSpace**). Values less than or equal to 0 are treated as the default value **1**.

**string** type: Only **'auto'** is supported. Child elements are laid out linearly based on their main-axis width without adapting to the **Swiper** component's width. [customContentTransition](#customcontenttransition) and [onContentDidScroll](#oncontentdidscroll) events are disabled.

**SwiperAutoFill** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The system automatically works out the number of elements per page based on the width and **minSize** settings of the **Swiper** component. If **minSize** is left empty or set to a value less than or equal to 0, the **Swiper** component displays one column.

> **NOTE:** 
> 
> - When turning pages by group is used, the drag distance threshold for turning pages is half of the width of the
> **Swiper** component (50% of the child elements width if turning pages by child element is used). If the number
> of child elements in the last group is less than the value of **displayCount**, placeholders are used, but they
> show the **Swiper** background style directly and do not display any content.
> 
> - When **displayCount** is set to **'auto'** and **loop** is set to **false**, the position of the selected navigation indicator aligns with the first page in the viewport. If the first page is only partially displayed in the viewport after switching, the selected navigation indicator remains aligned with the page's position, between two unselected indicators. In this case, you are advised to hide the navigation indicators.
> 
> - If the navigation indicator is in dot style, the number of displayed navigation dots equals the number of child elements when the number of child elements displayed in the viewport is 1 (single-page scenario) or
> **displayCount** is set to **'auto'**.
> 
> - If **displayCount** is set to **'auto'** and **swipeByGroup** is set to **true**, each child element will be treated as a group for page switching, allowing only one page to be switched at a time. In this case, you are advised not to set **swipeByGroup** or set **swipeByGroup** to **false**.
> 
> - This API can be called within attributeModifier since API version 18.

When the navigation indicator is set to dot style and the number of child elements displayed in the viewport is greater than 1 (multi-page scenario)&lt;!--RP1--&gt;&lt;!--RP1End--&gt;, the number of displayed navigation dots follows the rules below.

| Total Children Count  
> Visible Children Count|Swiping by Group Enabled|Loop Status|Number of Navigation
Dots Displayed| Description|

| ------------------------------------------ | ------------ | --------------- | -------------------------  
----------------------------------- | ---------------------------------------- |

| Yes | Yes | **loop** set to **true** | Equals the number of groups(calculated by dividing the total number of child elements by the number of visible child elements, with rounding up if there is a remainder).| Not effective when **displayCount** is set to **'auto'**.|

| Yes | Yes | **loop** set to **false**| Equals the number of groups (calculated by dividing the total number of child elements by the number of visible child elements, with rounding up if there is a remainder).| Not effective when **displayCount** is set to **'auto'**.|

| Yes | No | **loop** set to **true** | Equals the actual number of page turns available(that is, the total number of child elements).| —— |

| Yes | No | **loop** set to **false**| Equals the actual number of page turns available(calculated as total number of child elements minus the number of visible child elements, plus 1).| Not effective when **displayCount** is set to **'auto'**.|

| No (while the total number of child elements is greater than 0)| —— | —— | 1 |Not effective when **displayCount** is set to **'auto'**.|

| No (while the total number of child elements is 0)| —— | —— | 0| —— |

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [SwiperAutoFill](arkts-arkui-swiperautofill-i.md) | Yes | Number of elements to display per page.<br> Default value: **1**<br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used.<br>**Since:** 10 |
| swipeByGroup | boolean | No | Whether to turn pages by group. The value **true** means to turn pages by group, and **false** means to turn pages by child element. When turning pages by group is used, the number of child elements per group is the value of **displayCount**.<br> Default value: **false**.<br>**Since:** 11 |

## displayCount

```TypeScript
displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean)
```

Sets the number of elements to display per page.

**number** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The child elements are stretched or shrunk to equally divide the **Swiper** component's width (minus **displayCount-1** times **itemSpace**). Values less than or equal to 0 are treated as the default value **1**.

**string** type: Only **'auto'** is supported. Child elements are laid out linearly based on their main-axis width without adapting to the **Swiper** component's width. [customContentTransition](#customcontenttransition) and [onContentDidScroll](#oncontentdidscroll) events are disabled.

**SwiperAutoFill** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The system automatically works out the number of elements per page based on the width and **minSize** settings of the **Swiper** component. If **minSize** is left empty or set to a value less than or equal to 0, the **Swiper** component displays one column.

**ItemFillPolicy** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The number of displayed elements is determined based on the breakpoint type corresponding to the **Swiper** component's width. For example, if the breakpoint type is set to **ItemFillPolicy.BREAKPOINT_DEFAULT**, one column is displayed when the component width falls within the sm or smaller breakpoint range, two columns are displayed for the md breakpoint range, and three columns are displayed for the lg or a larger breakpoint range.

For details about the parameter, see [displayCount](#displaycount).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [SwiperAutoFill](arkts-arkui-swiperautofill-i.md) &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of elements to display per page.<br> The value range is (0, +∞). If the value is less than or equal to 0, the value **1** is used. |
| swipeByGroup | boolean | No | Whether to turn pages by group. The value **true** means to turn pages by group, and **false** means to turn pages by child element. When turning pages by group is used, the number of child elements per group is the value of **displayCount**.<br> Default value: **false**. |

## displayMode

```TypeScript
displayMode(value: SwiperDisplayMode)
```

Sets the mode in which elements are displayed along the main axis. This API takes effect only when [displayCount](#displaycount) is not set.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SwiperDisplayMode](arkts-arkui-swiperdisplaymode-e.md) | Yes | Mode in which elements are displayed along the main axis.<br>Default value: **SwiperDisplayMode.STRETCH** |

## duration

```TypeScript
duration(value: number)
```

Sets the duration of the animation for child component switching.

**duration** must be used in conjunction with [curve](#curve).

The default curve for the animation is [interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md). When this curve is applied, the duration of the animation is determined solely by the parameters of the curve itself and is no longer governed by the **duration** setting. For curves that are not governed by the **duration** setting, see [Interpolation Calculation](../arkts-apis/arkts-arkui-curves.md). Among others, [springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md), [responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md), and interpolatingSpring do not respect the **duration** setting. To have the animation duration managed by **duration**, you should select a different curve for the **curve** attribute.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Duration of the autoplay for child component switching.<br>Default value: **400**<br> Unit: ms<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

## effectMode

```TypeScript
effectMode(value: EdgeEffect)
```

Edge sliding effect. This parameter takes effect only when [loop](#loop) is set to **false** or all child nodes are displayed on one screen in the **Swiper** viewport. When the [SwiperController.changeIndex()](arkts-arkui-swipercontroller-c.md#changeindex), [SwiperController.showNext()](arkts-arkui-swipercontroller-c.md#shownext), or [SwiperController.showPrevious()](arkts-arkui-swipercontroller-c.md#showprevious) API is called to go to the first or last page, the rebound effect does not take effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the component is at one of the edges.<br>Default value: **EdgeEffect.Spring** |

## index

```TypeScript
index(value: number)
```

Sets the index of the child component currently displayed in the container.

Since API version 10, this attribute supports two-way binding through [&#36;&#36;](../../../ui/state-management/arkts-two-way-sync.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Index of the child component currently displayed in the container.<br>Default value: **0**<br>**NOTE:** <br>If the value specified is less than 0 or greater than the maximum page index, the value **0** is used. |

## indicator

```TypeScript
indicator(value: DotIndicator | DigitIndicator | boolean)
```

Sets the style of the navigation indicator.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DotIndicator](arkts-arkui-dotindicator-c.md) &#124; [DigitIndicator](arkts-arkui-digitindicator-c.md) &#124; boolean | Yes | Style of the navigation indicator.<br> - **DotIndicator**: dot-style indicator.<br> - **DigitIndicator**: digit-style indicator.<br> - **boolean**: whether to enable the navigation indicator. **true** to enable, **false** otherwise.<br> Default value: **true**<br> Default style: **DotIndicator**<br>**Since:** 10 |

## indicator

```TypeScript
indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean)
```

Sets the navigation indicator for the component.

> **NOTE:** 
> 
> An externally bound navigation indicator component can be used together if it is set. The display position and
> size can be customized for the external navigation indicator. For details, see
> Indicator.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indicator | [IndicatorComponentController](arkts-arkui-indicatorcomponentcontroller-c.md) &#124; [DotIndicator](arkts-arkui-dotindicator-c.md) &#124; [DigitIndicator](arkts-arkui-digitindicator-c.md) &#124; boolean | Yes | Style of the navigation indicator.<br>- **IndicatorComponentController**: separate navigation indicator controller. This controller can be bound to an external navigation indicator, but the external and internal indicators cannot coexist.<br> - **DotIndicator**: dot-style indicator.<br> - **DigitIndicator**: digit-style indicator.<br> - **boolean**: whether to enable the navigation indicator. **true** to enable, **false** otherwise.<br> Default value: **true**<br> Default style: **DotIndicator** |

## indicatorInteractive

```TypeScript
indicatorInteractive(value: boolean)
```

Sets whether the navigation indicator is interactive.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the navigation indicator is interactive.<br>The value **true** means that the navigation indicator is interactive, and **false** means the opposite.<br>If the input parameter is invalid, the value **true** is used. |

## indicatorStyle

```TypeScript
indicatorStyle(value?: IndicatorStyle)
```

Sets the style of the navigation indicator.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [indicator](#indicator)(value: DotIndicator | DigitIndicator | boolean)

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-indicatorstyle-i.md) | No | Style of the navigation indicator. |

## interval

```TypeScript
interval(value: number)
```

Sets the interval for automatic playback.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Interval for automatic playback. If the value is smaller than the value of [duration](#duration), the next carousel starts immediately after page switching completes.<br>Default value: **3000**.<br>Unit: ms<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

## itemSpace

```TypeScript
itemSpace(value: number | string)
```

Sets the space between child components. Percentage values are not supported.

If the type is number, the default unit is vp. If the type is string, the pixel unit must be explicitly specified, for example, **'10px'**; if the unit is not specified, for example, **'10'**, the default unit vp is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Space between child components.<br>Default value: **0**<br>Value range: [0, +∞). Values less than 0 or exceeding the **Swiper** component width are treated as the default value. |

## loop

```TypeScript
loop(value: boolean)
```

Sets whether to enable loop playback. In **LazyForEach** mode, it is recommended that the number of loaded components be greater than 5.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable loop playback.<br>**true**: yes; **false**: no<br>If the input parameter is invalid, the value **true** is used. |

## maintainVisibleContentPosition

```TypeScript
maintainVisibleContentPosition(enabled: boolean)
```

Sets whether to maintain the visible content position when data is inserted or deleted above or ahead of the viewport. This applies to **Swiper** components using a single [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) as the child node, where the data source is modified using **LazyForEach** API such as [onDataAdd](arkts-arkui-datachangelistener-i.md#ondataadd) or [onDataDelete](arkts-arkui-datachangelistener-i.md#ondatadelete). In other scenarios, the position of the visible content changes when data is inserted or deleted above or before the display area.

When **swipeByGroup** in [displayCount](#displaycount) is set to **true**, the visible content position remains unchanged only if the amount of data inserted or deleted above or before the display area is a multiple of the group size. Otherwise, the visible content position may change during group recalculation.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to maintain the visible content position when data is inserted or deleted above or ahead of the viewport.<br>Default value: **false**.<br>**false**: The visible content position will change when data is inserted or deleted. **true**: The visible content position remains unchanged when data is inserted or deleted. Animations stop if the data source is modified during an animation due to target index changes. |

## nestedScroll

```TypeScript
nestedScroll(value: SwiperNestedScrollMode)
```

Sets the nested scrolling mode of the **Swiper** component and its parent container. When [loop](#loop) is set to **true**, the **Swiper** component has no edge effect and does not trigger nested scrolling of its parent container.

> **NOTE:** 
> 
> The **Swiper** component's flick animation logic differs from other scrollable components, as **Swiper** can only
> slide one page at a time and performs a page-flip animation during a flick. When a **Swiper** component is nested
> with other scrollable components, it will not accept the scroll offset values transmitted by its child nodes
> after its page-turning animation has already started. At this point, the page-turning animation of the **Swiper**
> and the edge effect animation of the child node will be executed simultaneously.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SwiperNestedScrollMode](arkts-arkui-swipernestedscrollmode-e.md) | Yes | Nested scrolling mode of the **Swiper** component and its parent container.<br>If an invalid value is passed, the value **SwiperNestedScrollMode.SELF_ONLY** is used. |

## nextMargin

```TypeScript
nextMargin(value: Length, ignoreBlank?: boolean)
```

Sets the trailing margin to reveal a portion of the next item. For the implementation example, see [Example 1: Setting the Navigation Indicator Interaction and Page Turning Effect](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-1-setting-the-navigation-indicator-interaction-and-page-turning-effect). This attribute is effective only when the layout mode of the child components in **Swiper** is set to stretch, which mainly includes two scenarios: 1. **displayMode** is set to **SwiperDisplayMode.STRETCH**; 2. **displayCount** is assigned a numeric value.

When the main axis runs horizontally and either **nextMargin** or **prevMargin** is greater than the measured width of the child component, both margins are hidden.

When the main axis runs vertically and either **nextMargin** or **prevMargin** is greater than the measured height of the child component, both margins are hidden.

When using the **nextMargin** or **prevMargin** API, avoid applying size constraints to child components. Otherwise, the main axis of the child nodes will not be stretched to the expected length, causing the margins to lose their effect.

> **NOTE:** 
> 
> This API cannot be called within attributeModifier.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Trailing margin. Percentage values are not supported.<br>Default value: **0** |
| ignoreBlank | boolean | No | Whether to hide the trailing margin for the last page in non-loop scenarios.<br> **true**: Hide the trailing margin, in which case, the right edge of the last page is aligned with that of the **Swiper** component's viewable area.<br>**false**: Show the trailing margin, in which case, the last page has a **nextMargin**-specified gap from the **Swiper** component's right edge.<br>Default value: **false**.<br> **NOTE:** <br>On the last page, the values of **prevMargin** and **nextMargin** are added to create a left margin that allows the previous page to be displayed partially.<br>**Since:** 12 |

## onAnimationEnd

```TypeScript
onAnimationEnd(event: OnSwiperAnimationEndCallback)
```

Triggered when the page transition animation ends.

This event is triggered when the switching animation of the **Swiper** component ends, whether it is caused by gesture interruption or by calling **finishAnimation** through **SwiperController**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationEndCallback](arkts-arkui-onswiperanimationendcallback-t.md) | Yes | Callback triggered when the page transition animation ends.<br>**Since:** 18 |

## onAnimationStart

```TypeScript
onAnimationStart(event: OnSwiperAnimationStartCallback)
```

Triggered when the page transition animation starts.

> **NOTE:** 
> 
> - When this callback is invoked, the page transition animation logic is executed in the rendering thread,allowing the idle main thread to load resources required by child components. This reduces preloading time for nodes within the **cachedCount** range. For best practices, see [Optimizing Frame Loss During Swiper Component Loading — Preloading Data](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-swiper_high_performance_development_guide#section8783121513246).
> 
> 
> - When the duration of the page transition animation is set to **0**, this callback is triggered only in the following scenarios: swiping to turn pages, automatic playback, calling **SwiperController.showNext()** or
> **SwiperController.showPrevious()**, and touching navigation indicators to navigate.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationStartCallback](arkts-arkui-onswiperanimationstartcallback-t.md) | Yes | Callback triggered when the page transition animation starts.<br>**Since:** 18 |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Triggered when the index of the currently displayed element changes. The return value is the index of the currently displayed element.

When the **Swiper** component is used together with **LazyForEach**, the subpage UI update cannot be triggered in the **onChange** event.

> **NOTE:** 
> 
> If the index change is caused by an animation, this callback is triggered when the animation ends.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the currently displayed element.<br>**Since:** 18 |

## onContentDidScroll

```TypeScript
onContentDidScroll(handler: ContentDidScrollCallback)
```

Triggered when content in the **Swiper** component scrolls.

Instructions:

1. This API does not work when **prevMargin** and **nextMargin** are set in such a way that the **Swiper**
frontend and backend display the same page during loop playback.
2. During page scrolling, the [ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md) callback is invoked for
all pages in the viewport on a frame-by-frame basis. For example, when there are two pages whose subscripts are 0 and 1 in the viewport, two callbacks whose indexes are 0 and 1 are invoked in each frame.
3. When the **swipeByGroup** parameter of the **displayCount** attribute is set to **true**,
the callback is invoked for all pages in a group if any page in the group is within the viewport.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [ContentDidScrollCallback](arkts-arkui-contentdidscrollcallback-t.md) | Yes | Callback triggered when content in the **Swiper** component scrolls. |

## onContentWillScroll

```TypeScript
onContentWillScroll(handler: ContentWillScrollCallback)
```

Triggered when the **Swiper** component is about to scroll. This event allows you to intercept and control the scrolling behavior of the component. The component determines whether to allow the scroll action based on the return value. If **true** is returned, the scroll action is allowed, and the pages in the **Swiper** component will follow the scrolling. If **false** is returned, the scroll action is disallowed, and the pages will remain stationary.

1. This event is only triggered by gesture operations, including finger swipes,
scrolling the mouse wheel, and moving focus using keyboard arrow keys.

2. During finger swipes, the event is triggered for each frame.
The system uses the return value of the event to determine whether to respond to the swipe for each frame.

3. For scrolling the mouse wheel and moving focus using keyboard arrow keys,
the event is triggered once per page turning. The system uses the return value to decide whether to allow the page turning.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [ContentWillScrollCallback](arkts-arkui-contentwillscrollcallback-t.md) | Yes | Callback triggered when content in the **Swiper** component scrolls. |

## onGestureSwipe

```TypeScript
onGestureSwipe(event: OnSwiperGestureSwipeCallback)
```

Triggered on a frame-by-frame basis when the page is turned by a swipe.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnSwiperGestureSwipeCallback](arkts-arkui-onswipergestureswipecallback-t.md) | Yes | Callback triggered on a frame-by-frame basis when the page is turned by a swipe. **onGestureSwipe** is called after **onTouch**. For post-release operations, consider using [onAnimationStart](#onanimationstart).<br>**Since:** 18 |

## onScrollStateChanged

```TypeScript
onScrollStateChanged(event: Callback<ScrollState>)
```

Defines the callback of the swipe state change event for the **Swiper** component. This callback is triggered when the swipe state changes across the followings: scrolling with the touch, animating after release, and stopped.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[ScrollState](arkts-arkui-scrollstate-e.md)&gt; | Yes | Callback triggered when the sliding status changes. |

## onSelected

```TypeScript
onSelected(event: Callback<number>)
```

Triggered when the selected element changes. The index of the currently selected element is returned.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the currently selected element. |

## onUnselected

```TypeScript
onUnselected(event: Callback<number>)
```

Triggered when the selected element changes. The index of the element that is about to be hidden is returned.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;number&gt; | Yes | Index of the element that is about to be hidden. |

## pageFlipMode

```TypeScript
pageFlipMode(mode: Optional<PageFlipMode>)
```

Sets the mode for flipping pages using the mouse wheel. If this API is not used, the continuous page flipping mode (specified by value **PageFlipMode.CONTINUOUS**) is used by default.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;[PageFlipMode](../arkts-apis/arkts-arkui-pageflipmode-e.md)&gt; | Yes | Mode for flipping pages using the mouse wheel.<br>If the value is **undefined**, the value **PageFlipMode.CONTINUOUS** is used. |

## prevMargin

```TypeScript
prevMargin(value: Length, ignoreBlank?: boolean)
```

Sets the leading margin to reveal a portion of the previous item. For the implementation example, see [Example 1: Setting the Navigation Indicator Interaction and Page Turning Effect](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-1-setting-the-navigation-indicator-interaction-and-page-turning-effect). This attribute is effective only when the layout mode of the child components in **Swiper** is set to stretch, which mainly includes two scenarios: 1. **displayMode** is set to **SwiperDisplayMode.STRETCH**; 2. **displayCount** is assigned a numeric value.

When the main axis runs horizontally and either **nextMargin** or **prevMargin** is greater than the measured width of the child component, both margins are hidden.

When the main axis runs vertically and either **nextMargin** or **prevMargin** is greater than the measured height of the child component, both margins are hidden.

When using the **nextMargin** or **prevMargin** API, avoid applying size constraints to child components. Otherwise, the main axis of the child nodes will not be stretched to the expected length, causing the margins to lose their effect.

> **NOTE:** 
> 
> This API cannot be called within attributeModifier.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Leading margin. Percentage values are not supported.<br>Default value: **0** |
| ignoreBlank | boolean | No | Whether to hide the leading margin for the first page in non-loop scenarios.<br> **true**: Hide the leading margin, in which case, the left edge of the first page is aligned with that of the **Swiper** component's viewable area.<br>**false**: Show the leading margin, in which case, the first page has a **prevMargin**-specified gap from the **Swiper** component's left edge.<br>Default value: **false**.<br> **NOTE:** <br>On the first page, the values of **prevMargin** and **nextMargin** are added to create a right margin that allows the next page to be displayed partially.<br>**Since:** 12 |

## vertical

```TypeScript
vertical(value: boolean)
```

Sets whether vertical swiping is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether vertical swiping is used. The value **true** means vertical swiping, and **false** means horizontal swiping.<br>Default value: **false**. |
