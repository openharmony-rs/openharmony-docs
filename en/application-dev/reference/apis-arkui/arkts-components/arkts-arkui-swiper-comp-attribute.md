# Swiper properties/events

```TypeScript
declare class SwiperAttribute extends CommonMethod<SwiperAttribute>
```

In addition to the [universal attributes](arkts-arkui-common-comp.md), the following attributes are supported.

In addition to the [universal events](arkts-arkui-common-comp.md), the following events are supported.

**Inheritance/Implementation:** SwiperAttribute extends CommonMethod&lt;SwiperAttribute&gt;

**Since:** 7

<!--Device-unnamed-declare class SwiperAttribute extends CommonMethod<SwiperAttribute>--><!--Device-unnamed-declare class SwiperAttribute extends CommonMethod<SwiperAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="autoplay1"></a>

## autoPlay

```TypeScript
autoPlay(value: boolean)
```

Sets whether to enable automatic playback for child components, with the direction from the smallest to largest index.

When [loop](#loop) is set to **false**, auto play stops when the last page is reached. After a gesture switch is completed, if the current page is not the last page, auto play continues. Auto play also stops when the **Swiper** is invisible.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-autoPlay(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-autoPlay(value: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable automatic playback for child components.<br>**true**: yes; **false**: no <br>If an invalid value is passed, the value **false** is used. |

<a id="autoplay2"></a>

## autoPlay

```TypeScript
autoPlay(autoPlay: boolean, options: AutoPlayOptions)
```

Sets whether to enable automatic playback for child components. The **options** input parameter controls whether automatic playback stops when a finger or mouse presses the screen.

If [loop](#loop) is set to **false**, automatic playback stops at the last page and resumes after navigated away from the last page using gestures. Automatic playback also stops when the **Swiper** component is not visible.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-SwiperAttribute-autoPlay(autoPlay: boolean, options: AutoPlayOptions): SwiperAttribute--><!--Device-SwiperAttribute-autoPlay(autoPlay: boolean, options: AutoPlayOptions): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| autoPlay | boolean | Yes | Whether to enable automatic playback for child components.<br>**true**: yes; **false**: no <br>If an invalid value is passed, the value **false** is used. |
| options | [AutoPlayOptions](arkts-arkui-swiper-comp-autoplayoptions-i.md) | Yes | Whether child components stop automatic playback when the screen is pressed by fingers, a mouse device, or other input devices. If **stopWhenTouched** is set to **true**, automatic playback resumes after any finger lifts in multi-touch scenarios.<br>Default value: **{ stopWhenTouched: true }**. |

<a id="cachedcount1"></a>

## cachedCount

```TypeScript
cachedCount(value: number)
```

Sets the number of child components to be preloaded. Based on the current page, the child components before and after the current displayed page are loaded. When an item before the current page is deleted, the items after it shift forward to fill the gap. For example, when **cachedCount** is set to **1**, the child components of the previous page and the next page adjacent to the current displayed page in index order are preloaded. If group-based page turning is set, that is, the **swipeByGroup** parameter of **displayCount** is set to true, preloading is performed in groups. For example, when **cachedCount** is set to **1** and **swipeByGroup** is set to **true**, the child components of the group before and the group after the current group are preloaded.

> **NOTE:** 
> 
> - In continuous scrolling scenarios where one **Swiper** child component is displayed per screen, setting
> **cachedCount** to **1** or **2** is typically sufficient. For best practices, see
> [Optimizing Frame Loss During Swiper Component Loading – Caching Data Items](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-swiper_high_performance_development_guide#section143504547145).
> 
> - This parameter takes effect only when used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or the [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) component that has virtualScroll enabled. Child components outside the visible area and cache range will be released after this parameter takes effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-cachedCount(value: number): SwiperAttribute--><!--Device-SwiperAttribute-cachedCount(value: number): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of child components to be preloaded (cached).<br>Default value: **1** <br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

<a id="cachedcount2"></a>

## cachedCount

```TypeScript
cachedCount(count: number, isShown: boolean)
```

Sets the number of child components to be cached.

> **NOTE:** 
> 
> - This attribute takes effect only in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) with the **virtualScroll** switch enabled. After it takes effect, child nodes beyond the cache range are released.
> 
> - When **isShown** is set to **true** and **count** is set to a large value, if the nodes that can be loaded within the preloading range before and after are insufficient, the same loadable node is laid out on only one side in a loop scenario.

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-SwiperAttribute-cachedCount(count: number, isShown: boolean): SwiperAttribute--><!--Device-SwiperAttribute-cachedCount(count: number, isShown: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of child components to be preloaded (cached).<br>Default value: **1** <br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |
| isShown | boolean | Yes | Whether the cached nodes within the range are rendered without being added to the render tree.<br>**true**: yes; **false**: no <br>If an invalid value is passed, the value **false** is used. |

<a id="cachedcount3"></a>

## cachedCount

```TypeScript
cachedCount(count: number, options: CachedCountOptions)
```

Sets the number of child components to be preloaded and configuration options.

> **NOTE:** 
> 
> - When **independent** in options is set to **true**, the number of preloaded child components is calculated based on the value of **count**, which is decoupled from the **swipeByGroup** calculation of [displayCount](#displaycount2).For example, if the value of **count** in **cachedCount** is **1**, the previous and next child components of the current child node are preloaded.
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

<!--Device-SwiperAttribute-cachedCount(count: number, options: CachedCountOptions): SwiperAttribute--><!--Device-SwiperAttribute-cachedCount(count: number, options: CachedCountOptions): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of child components to preload.<br>Default value: **1**<br>Value range: [0, +∞). If a value less than 0 is set, 1 is used. |
| options | [CachedCountOptions](arkts-arkui-swiper-comp-cachedcountoptions-i.md) | Yes | Configuration options for preloading child components. The object properties include **isShown** (whether to draw nodes within the preload range) and **independent** (whether to calculate based on the actual number of child components). |

## curve

```TypeScript
curve(value: Curve | string | ICurve)
```

Sets the animation curve. The interpolating spring curve is used by default. For details about common curves, see Curve. You can also create custom curves (interpolation curve objects) by using the API provided by the [interpolation calculation](../arkts-apis/arkts-arkui-curves.md) module.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-curve(value: Curve | string | ICurve): SwiperAttribute--><!--Device-SwiperAttribute-curve(value: Curve | string | ICurve): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | Curve &#124; string &#124; ICurve | Yes | Animation curve. <br>The **string** type is deprecated since API version 9 (see [curves.init](../arkts-apis/arkts-arkui-curves-init-f.md), [curves.steps](../arkts-apis/arkts-arkui-curves-steps-f.md), [curves.cubicBezier](../arkts-apis/arkts-arkui-curves-cubicbezier-f.md), and [curves.spring](../arkts-apis/arkts-arkui-curves-spring-f.md)). Use **Curve** or **ICurve** instead. <br>Default value: **[interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md)(-1, 1, 328, 34)**.<br>**Since:** 10 |

## customContentTransition

```TypeScript
customContentTransition(transition: SwiperContentAnimatedTransition)
```

Defines a custom page transition animation. During finger-following swipes and post-release transition animations, this triggers a frame-by-frame callback for all pages in the viewport, allowing you to customize animations by modifying properties like opacity, scale, and translation.

Instructions:

1) In a loop scenario, when the **prevMargin** and **nextMargin** attributes are set so that the front and rear areas of the **Swiper** viewport display the same page, this API does not take effect. 2) During finger-following swiping and the switch animation after the finger is released, the [SwiperContentTransitionProxy](arkts-arkui-swiper-comp-swipercontenttransitionproxy-i.md) callback is triggered frame by frame for all pages in the viewport. For example, when there are two pages with indexes **0** and **1** in the viewport, the callback is triggered twice per frame, with the index values **0** and **1** respectively. 3) When the **swipeByGroup** parameter of the **displayCount** attribute is set to **true**, if at least one page in the same group is in the viewport, the callback is triggered for all pages in the group; if no page in the group is in the viewport, all pages in the group are removed from the render tree together. 4) During finger-following swiping and the switch animation after the finger is released, the default animation (page sliding) still occurs. If you want the page not to slide, you can set a negative displacement (translate attribute) along the main axis to offset the page sliding. For example, when the **displayCount** attribute value is 2 and there are two pages with indexes 0 and 1 in the viewport, during horizontal page sliding, you can set the translate attribute of page 0 on the x-axis to -position * mainAxisLength frame by frame to offset the displacement of page 0, and set the **translate** attribute of page 1 on the x-axis to -(position - 1) * mainAxisLength to offset the displacement of page 1.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**Widget capability:** This API can be used in ArkTS widgets since API version 26.0.0.

<!--Device-SwiperAttribute-customContentTransition(transition: SwiperContentAnimatedTransition): SwiperAttribute--><!--Device-SwiperAttribute-customContentTransition(transition: SwiperContentAnimatedTransition): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| transition | [SwiperContentAnimatedTransition](arkts-arkui-swiper-comp-swipercontentanimatedtransition-i.md) | Yes | Information about the custom transition animation of **Swiper**. The object attributes include **timeout** (timeout duration) and **transition** (callback for the specific content of the custom transition animation). |

## disableSwipe

```TypeScript
disableSwipe(value: boolean)
```

Sets whether to disable the component swipe switching feature. This is applicable to scenarios where page turning is controlled only by buttons or navigation dots, or where user swipe operations need to be restricted.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-disableSwipe(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-disableSwipe(value: boolean): SwiperAttribute-End-->

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

<!--Device-SwiperAttribute-displayArrow(value: ArrowStyle | boolean, isHoverShow?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-displayArrow(value: ArrowStyle | boolean, isHoverShow?: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ArrowStyle](arkts-arkui-swiper-comp-arrowstyle-i.md) &#124; boolean | Yes | Arrow and background to set. In cases of exceptions, the default values in the **ArrowStyle** object are used. The value **true** means to show the arrow and background in the default styles, and **false** means to hide the arrow and background.<br>Default value: **false**. |
| isHoverShow | boolean | No | Whether to show the arrow on mouse hover.<br>Default value: **false**. <br>**NOTE:** <br>1. **false**: The arrow is always displayed. <br>2. **true**: The arrow is displayed. <br>With navigation indicators, the arrow is displayed when the mouse pointer hovers over the indicators or arrow areas. <br>Without navigation indicators, the arrow is displayed when the mouse pointer hovers over the **Swiper** display area. <br>3. When the arrow is displayed, clicking the arrow turns pages. |

<a id="displaycount1"></a>

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
> - This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 18.When the navigation indicator is set to dot style and the number of child elements displayed in the viewport is greater than 1 (multi-page scenario)<!--RP1--><!--RP1End-->, the number of displayed navigation dots follows the rules below.

| Total Children Count Visible Children Count| Swiping by Group Enabled| Loop Status | Number of Navigation Dots Displayed | Description |

| ------------------------------------------ | ------------ | --------------- | ------------------------------------------------------------ | ---------------------------------------- |  
| Yes | Yes | **loop** set to **true** | Equals the number of groups (calculated by dividing the total number of child elements by the number of visible child elements, with rounding up if there is a remainder).| Not effective when **displayCount** is set to **'auto'**.|  
| Yes | Yes | **loop** set to **false**| Equals the number of groups (calculated by dividing the total number of child elements by the number of visible child elements, with rounding up if there is a remainder).| Not effective when **displayCount** is set to **'auto'**.|
| Yes | No | **loop** set to **true** | Equals the actual number of page turns available (that is, the total number of child elements).| —— |
| Yes | No | **loop** set to **false**| Equals the actual number of page turns available (calculated as total number of child elements minus the number of visible child elements, plus 1).| Not effective when **displayCount** is set to **'auto'**.|
| No (while the total number of child elements is greater than 0) | —— | —— | 1 | Not effective when **displayCount** is set to **'auto'**.|
| No (while the total number of child elements is 0)| —— | —— | 0| —— |

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill, swipeByGroup?: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [SwiperAutoFill](arkts-arkui-swiper-comp-swiperautofill-i.md) | Yes | Number of elements to display per page.<br> Default value: **1** <br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used.<br>**Since:** 10 |
| swipeByGroup | boolean | No | Whether to turn pages by group. If set to **true**, pages are turned by group, and the number of child elements in each group is the value of **displayCount**. If set to **false**, the default page turning behavior is used, that is, pages are turned by child element.<br>Default value: **false** <br><br>**Since:** 11 |

<a id="displaycount2"></a>

## displayCount

```TypeScript
displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean)
```

Sets the number of elements to display per page.

**number** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The child elements are stretched or shrunk to equally divide the **Swiper** component's width (minus **displayCount-1** times **itemSpace**). Values less than or equal to 0 are treated as the default value **1**.

**string** type: Only **'auto'** is supported. Child elements are laid out linearly based on their main-axis width without adapting to the **Swiper** component's width. [customContentTransition](#customcontenttransition) and [onContentDidScroll](#oncontentdidscroll) events are disabled.

**SwiperAutoFill** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The system automatically works out the number of elements per page based on the width and **minSize** settings of the **Swiper** component. If **minSize** is left empty or set to a value less than or equal to 0, the **Swiper** component displays one column.

**ItemFillPolicy** type: Child elements' main-axis width adapts to the **Swiper** component's main-axis width. The number of displayed elements is determined based on the breakpoint type corresponding to the **Swiper** component's width. For example, if the breakpoint type is set to **ItemFillPolicy.BREAKPOINT_DEFAULT**, one column is displayed when the component width falls within the sm or smaller breakpoint range, two columns are displayed for the md breakpoint range, and three columns are displayed for the lg or a larger breakpoint range.

For details about the parameter, see [displayCount](#displaycount1).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-displayCount(value: number | string | SwiperAutoFill | ItemFillPolicy, swipeByGroup?: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [SwiperAutoFill](arkts-arkui-swiper-comp-swiperautofill-i.md) &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of child components displayed in the viewport.<br>Default value: **1**<br>Value range: (0, +∞). If the value is set to less than or equal to 0, it is processed as 1. |
| swipeByGroup | boolean | No | Whether to turn pages by group. The value **true** means to turn pages by group, and **false** means to turn pages by child element. When turning pages by group is used, the number of child elements per group is the value of **displayCount**.<br> Default value: **false**. |

## displayMode

```TypeScript
displayMode(value: SwiperDisplayMode)
```

Sets the mode in which elements are displayed along the main axis. This API takes effect only when [displayCount](#displaycount1) is not set.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-displayMode(value: SwiperDisplayMode): SwiperAttribute--><!--Device-SwiperAttribute-displayMode(value: SwiperDisplayMode): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SwiperDisplayMode](arkts-arkui-swiper-comp-swiperdisplaymode-e.md) | Yes | Mode in which elements are displayed along the main axis.<br>Default value: **SwiperDisplayMode.STRETCH** |

## duration

```TypeScript
duration(value: number)
```

Sets the duration of the animation for child component switching.

**duration** must be used in conjunction with [curve](#curve).

The default curve for the animation is [interpolatingSpring](../arkts-apis/arkts-arkui-curves-interpolatingspring-f.md). When this curve is applied, the duration of the animation is determined solely by the parameters of the curve itself and is no longer governed by the **duration** setting. For curves that are not governed by the **duration** setting, see [Interpolation Calculation](../arkts-apis/arkts-arkui-curves.md). Among others, [springMotion](../arkts-apis/arkts-arkui-curves-springmotion-f.md), [responsiveSpringMotion](../arkts-apis/arkts-arkui-curves-responsivespringmotion-f.md), and interpolatingSpring do not respect the **duration** setting. To have the animation duration managed by **duration**, you should select a different curve for the **curve** attribute.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwiperAttribute-duration(value: number): SwiperAttribute--><!--Device-SwiperAttribute-duration(value: number): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Animation duration for switching between child components.<br>Default value: **400**<br/ >Unit: ms<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

## effectMode

```TypeScript
effectMode(value: EdgeEffect)
```

Edge sliding effect. This parameter takes effect only when [loop](#loop) is set to **false** or all child nodes are displayed on one screen in the **Swiper** viewport. When the [SwiperController.changeIndex()](arkts-arkui-swiper-comp-swipercontroller-c.md#changeindex1), [SwiperController.showNext()](arkts-arkui-swiper-comp-swipercontroller-c.md#shownext), or [SwiperController.showPrevious()](arkts-arkui-swiper-comp-swipercontroller-c.md#showprevious) API is called to go to the first or last page, the rebound effect does not take effect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-effectMode(value: EdgeEffect): SwiperAttribute--><!--Device-SwiperAttribute-effectMode(value: EdgeEffect): SwiperAttribute-End-->

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

Since API version 10, this attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-index(value: number): SwiperAttribute--><!--Device-SwiperAttribute-index(value: number): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Index of the child component currently displayed in the container.<br>Default value: **0** <br>**NOTE:** <br>If the value specified is less than 0 or greater than the maximum page index, the value **0** is used. |

<a id="indicator1"></a>

## indicator

```TypeScript
indicator(value: DotIndicator | DigitIndicator | boolean)
```

Sets the style of the navigation indicator.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-indicator(value: DotIndicator | DigitIndicator | boolean): SwiperAttribute--><!--Device-SwiperAttribute-indicator(value: DotIndicator | DigitIndicator | boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) &#124; [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) &#124; boolean | Yes | Style of the navigation indicator.<br> - **DotIndicator**: dot-style indicator. <br> - **DigitIndicator**: digit-style indicator. <br> - **boolean**: whether to enable the navigation indicator. **true** to enable, **false** otherwise. <br>Default value: **true**. <br>Default type: **DotIndicator**<br>**Since:** 10 |

<a id="indicator2"></a>

## indicator

```TypeScript
indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean)
```

Sets the navigation indicator for the component.

> **NOTE:** 
> 
> An externally bound navigation indicator component can be used together if it is set. The display position and
> size can be customized for the external navigation indicator. For details, see
> [Indicator](arkts-arkui-indicatorcomponent-comp.md).

**Since:** 15

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 15.

**Widget capability:** This API can be used in ArkTS widgets since API version 15.

<!--Device-SwiperAttribute-indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean): SwiperAttribute--><!--Device-SwiperAttribute-indicator(indicator: IndicatorComponentController | DotIndicator | DigitIndicator | boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| indicator | [IndicatorComponentController](arkts-arkui-indicatorcomponent-comp-indicatorcomponentcontroller-c.md) &#124; [DotIndicator](arkts-arkui-swiper-comp-dotindicator-c.md) &#124; [DigitIndicator](arkts-arkui-swiper-comp-digitindicator-c.md) &#124; boolean | Yes | Style of the navigation indicator.<br>- **IndicatorComponentController**: separate navigation indicator controller. This controller can be bound to an external navigation indicator, but the external and internal indicators cannot coexist. <br> - **DotIndicator**: dot-style indicator. <br> - **DigitIndicator**: digit-style indicator. <br> - **boolean**: whether to enable the navigation indicator. **true** to enable, **false** otherwise. <br>Default value: **true**. <br>Default type: **DotIndicator** |

## indicatorInteractive

```TypeScript
indicatorInteractive(value: boolean)
```

Sets whether the navigation dot is interactive. This is applicable to scenarios where page turning needs to be controlled through other means (such as a button), or where users need to be prevented from turning pages by tapping the navigation dot.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwiperAttribute-indicatorInteractive(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-indicatorInteractive(value: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the navigation indicator is interactive.<br>The value **true** means that the navigation indicator is interactive, and **false** means the opposite. <br>If the input parameter is invalid, the value **true** is used. |

## interval

```TypeScript
interval(value: number)
```

Sets the interval for automatic playback.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-interval(value: number): SwiperAttribute--><!--Device-SwiperAttribute-interval(value: number): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Time interval for auto play. When this value is less than the [duration](#duration) attribute value, the next auto play starts immediately after the page turn is complete.<br>Default value: **3000**<br>Unit: ms<br>Value range: [0, +∞). If a value less than 0 is set, the default value is used. |

## itemSpace

```TypeScript
itemSpace(value: number | string)
```

Sets the space between child components. Percentage values are not supported.

If the type is number, the default unit is vp. If the type is string, the pixel unit must be explicitly specified, for example, **'10px'**; if the unit is not specified, for example, **'10'**, the default unit vp is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-itemSpace(value: number | string): SwiperAttribute--><!--Device-SwiperAttribute-itemSpace(value: number | string): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Space between child components.<br>Default value: **0** <br>Value range: [0, +∞). Values less than 0 or exceeding the **Swiper** component width are treated as the default value. |

## loop

```TypeScript
loop(value: boolean)
```

Sets whether to enable looping. In the **LazyForEach** lazy loop loading mode, it is recommended that the number of loaded components be greater than 5. When the number of preloaded components is insufficient, blank areas or lag may occur during rapid switching.

> **NOTE:** 
> 
> In a loop scenario, when the **prevMargin**\/**nextMargin** attributes are set, linear traversal of child
> components by the screen reader triggers an infinite loop of "focus-scroll-expose new child node". In this
> scenario, you are advised to set **loop** to **false** or use
> [accessibilityGroup](arkts-arkui-common-comp-commonmethod-c.md#accessibilitygroup2)
> to disable accessibility services for child components.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-loop(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-loop(value: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable loop playback.<br>**true**: yes; **false**: no <br>If the input parameter is invalid, the value **true** is used. |

## maintainVisibleContentPosition

```TypeScript
maintainVisibleContentPosition(enabled: boolean)
```

Sets whether to maintain the visible content position when data is inserted or deleted above or ahead of the viewport. This applies to **Swiper** components using a single [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) as the child node, where the data source is modified using **LazyForEach** API such as [onDataAdd](arkts-arkui-lazyforeach-comp-datachangelistener-i.md#ondataadd) or [onDataDelete](arkts-arkui-lazyforeach-comp-datachangelistener-i.md#ondatadelete). In other scenarios, the position of the visible content changes when data is inserted or deleted above or before the display area.

When **swipeByGroup** in [displayCount](#displaycount1) is set to **true**, the visible content position remains unchanged only if the amount of data inserted or deleted above or before the display area is a multiple of the group size. Otherwise, the visible content position may change during group recalculation.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-SwiperAttribute-maintainVisibleContentPosition(enabled: boolean): SwiperAttribute--><!--Device-SwiperAttribute-maintainVisibleContentPosition(enabled: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to maintain the visible content position when data is inserted or deleted above or ahead of the viewport.<br>Default value: **false**. <br>**false**: The visible content position will change when data is inserted or deleted. **true**: The visible content position remains unchanged when data is inserted or deleted. Animations stop if the data source is modified during an animation due to target index changes. |

## nestedScroll

```TypeScript
nestedScroll(value: SwiperNestedScrollMode)
```

Sets the nested scroll mode between the **Swiper** component and its parent component. When the **Swiper** is nested in a scrollable container (such as **List** or **Scroll**), select an appropriate nested scroll mode based on business requirements. When [loop](#loop) is set to **true**, the **Swiper** component has no edge and does not trigger nested scrolling of the parent component.

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

<!--Device-SwiperAttribute-nestedScroll(value: SwiperNestedScrollMode): SwiperAttribute--><!--Device-SwiperAttribute-nestedScroll(value: SwiperNestedScrollMode): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [SwiperNestedScrollMode](arkts-arkui-swiper-comp-swipernestedscrollmode-e.md) | Yes | Nested scrolling mode of the **Swiper** component and its parent container.<br>If an invalid value is passed, the value **SwiperNestedScrollMode.SELF_ONLY** is used. |

## nextMargin

```TypeScript
nextMargin(value: Length, ignoreBlank?: boolean)
```

Sets the trailing margin to expose a small part of the next item. For the usage effect, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-1-setting-the-navigation-indicator-interaction-and-page-turning-effect). This attribute takes effect only when the layout mode of the Swiper child components is stretch, which mainly includes two scenarios: 1. The **displayMode** attribute is set to **SwiperDisplayMode.STRETCH**; 2. The **displayCount** attribute is set to the number type.

When the main axis runs horizontally and either **nextMargin** or **prevMargin** is greater than the measured width of the child component, both margins are hidden.

When the main axis runs vertically and either **nextMargin** or **prevMargin** is greater than the measured height of the child component, both margins are hidden.

When using the **nextMargin**\/**prevMargin** API, do not set the [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) attribute for child components. Otherwise, the child node will not be stretched to the expected length along the main axis, and the margin will lose its effect.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwiperAttribute-nextMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-nextMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Trailing margin. Percentage values are not supported.<br>Default value: **0**<br>The unit is described in [Length](../arkts-apis/arkts-arkui-length-t.md). |
| ignoreBlank | boolean | No | Whether to hide the **nextMargin** on the last page in non-loop scenarios.<br> **true**: The last page does not display the blank **nextMargin**, and the right edge of the last page is aligned with the right edge of the **Swiper** viewport.<br>**false**: The last page displays the blank **nextMargin**, and the distance between the right edge of the last page and the right edge of the **Swiper** viewport is **nextMargin**.<br>Default value: **false**.<br>**NOTE:** <br>On the last page, the values of **prevMargin** and **nextMargin** are added together and used as the left margin to display the previous page.<br>**Since:** 12 |

## onAnimationEnd

```TypeScript
onAnimationEnd(event: OnSwiperAnimationEndCallback)
```

Triggered when the page transition animation ends.

This event is triggered when the switching animation of the **Swiper** component ends, whether it is caused by gesture interruption or by calling **finishAnimation** through **SwiperController**.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-onAnimationEnd(event: OnSwiperAnimationEndCallback): SwiperAttribute--><!--Device-SwiperAttribute-onAnimationEnd(event: OnSwiperAnimationEndCallback): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationEndCallback](arkts-arkui-swiper-comp-onswiperanimationendcallback-t.md) | Yes | Callback triggered when the page transition animation ends.<br>**Since:** 18 |

## onAnimationStart

```TypeScript
onAnimationStart(event: OnSwiperAnimationStartCallback)
```

Triggered when the page transition animation starts.

> **NOTE:** 
> 
> - When this callback is invoked, the page transition animation logic is executed in the rendering thread,allowing the idle main thread to load resources required by child components. This reduces preloading time for nodes within the **cachedCount** range. For best practices, see [Optimizing Frame Loss During Swiper Component Loading – Preloading Data](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-swiper_high_performance_development_guide#section8783121513246).
> 
> - When the duration of the page transition animation is set to **0**, this callback is triggered only in the following scenarios: swiping to turn pages, automatic playback, calling **SwiperController.showNext()** or
> **SwiperController.showPrevious()**, and touching navigation indicators to navigate.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-onAnimationStart(event: OnSwiperAnimationStartCallback): SwiperAttribute--><!--Device-SwiperAttribute-onAnimationStart(event: OnSwiperAnimationStartCallback): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnSwiperAnimationStartCallback](arkts-arkui-swiper-comp-onswiperanimationstartcallback-t.md) | Yes | Callback triggered when the page transition animation starts.<br>**Since:** 18 |

## onChange

```TypeScript
onChange(event: Callback<number>)
```

Triggered when the index of the currently displayed element changes. The return value is the index of the currently displayed element.

When the **Swiper** component is used together with **LazyForEach**, the subpage UI update cannot be triggered in the **onChange** event.

> **NOTE:** 
> 
> - If the index change is caused by an animation, the callback is triggered when the animation ends.
> 
> - Difference from onSelected: onSelected is triggered immediately when the selected state changes, while onChange is triggered after the animation ends.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-onChange(event: Callback<number>): SwiperAttribute--><!--Device-SwiperAttribute-onChange(event: Callback<number>): SwiperAttribute-End-->

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

1) In a loop scenario, when the **prevMargin** and **nextMargin** attributes are set so that the front and rear areas of the Swiper viewport display the same page, this API does not take effect. 2) During page sliding, the [ContentDidScrollCallback](arkts-arkui-swiper-comp-contentdidscrollcallback-t.md) callback is triggered frame by frame for all pages in the viewport. For example, when there are two pages with indexes 0 and 1 in the viewport, the callback is triggered twice per frame, with the index values **0** and **1** respectively. 3) When the **swipeByGroup** parameter of the **displayCount** attribute is set to **true**, if at least one page in the same group is in the viewport, the callback is triggered for all pages in the group.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-SwiperAttribute-onContentDidScroll(handler: ContentDidScrollCallback): SwiperAttribute--><!--Device-SwiperAttribute-onContentDidScroll(handler: ContentDidScrollCallback): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [ContentDidScrollCallback](arkts-arkui-swiper-comp-contentdidscrollcallback-t.md) | Yes | Callback triggered when content in the **Swiper** component scrolls. |

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

<!--Device-SwiperAttribute-onContentWillScroll(handler: ContentWillScrollCallback): SwiperAttribute--><!--Device-SwiperAttribute-onContentWillScroll(handler: ContentWillScrollCallback): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [ContentWillScrollCallback](arkts-arkui-swiper-comp-contentwillscrollcallback-t.md) | Yes | Callback invoked when the **Swiper** is swiped. The value **true** indicates that swiping is allowed, and **false** indicates that swiping is not allowed. |

## onGestureSwipe

```TypeScript
onGestureSwipe(event: OnSwiperGestureSwipeCallback)
```

Triggered on a frame-by-frame basis when the page is turned by a swipe.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwiperAttribute-onGestureSwipe(event: OnSwiperGestureSwipeCallback): SwiperAttribute--><!--Device-SwiperAttribute-onGestureSwipe(event: OnSwiperGestureSwipeCallback): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnSwiperGestureSwipeCallback](arkts-arkui-swiper-comp-onswipergestureswipecallback-t.md) | Yes | Callback triggered frame by frame during the finger-following swipe of the page. The onGestureSwipe callback is triggered after onTouch. If you need to perform an operation when the animation starts after the finger leaves the screen, use [onAnimationStart](#onanimationstart).<br>**Since:** 18 |

## onScrollStateChanged

```TypeScript
onScrollStateChanged(event: Callback<ScrollState>)
```

Defines the callback of the swipe state change event for the **Swiper** component. This callback is triggered when the swipe state changes across the followings: scrolling with the touch, animating after release, and stopped.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**Widget capability:** This API can be used in ArkTS widgets since API version 20.

<!--Device-SwiperAttribute-onScrollStateChanged(event: Callback<ScrollState>): SwiperAttribute--><!--Device-SwiperAttribute-onScrollStateChanged(event: Callback<ScrollState>): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | Callback&lt;[ScrollState](arkts-arkui-list-comp-scrollstate-e.md)&gt; | Yes | Callback triggered when the sliding status changes. |

## onSelected

```TypeScript
onSelected(event: Callback<number>)
```

Triggered when the selected element changes. The index of the currently selected element is returned.

> **NOTE:** 
> 
> - In the **onSelected** callback, you cannot modify the index attribute of the swiper, and cannot call the
> **SwiperController.changeIndex()**, **SwiperController.showNext()**, and **SwiperController.showPrevious()**
> methods.
> 
> - Difference from **onChange**: **onSelected** is triggered immediately when the selected state changes, while
> **onChange** is triggered after the animation ends.

**Since:** 18

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 18.

**Widget capability:** This API can be used in ArkTS widgets since API version 18.

<!--Device-SwiperAttribute-onSelected(event: Callback<number>): SwiperAttribute--><!--Device-SwiperAttribute-onSelected(event: Callback<number>): SwiperAttribute-End-->

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

<!--Device-SwiperAttribute-onUnselected(event: Callback<number>): SwiperAttribute--><!--Device-SwiperAttribute-onUnselected(event: Callback<number>): SwiperAttribute-End-->

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

<!--Device-SwiperAttribute-pageFlipMode(mode: Optional<PageFlipMode>): SwiperAttribute--><!--Device-SwiperAttribute-pageFlipMode(mode: Optional<PageFlipMode>): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[PageFlipMode](../arkts-apis/arkts-arkui-pageflipmode-e.md)&gt; | Yes | Mode for flipping pages using the mouse wheel.<br>If the value is **undefined**, the value **PageFlipMode.CONTINUOUS** is used. |

## prevMargin

```TypeScript
prevMargin(value: Length, ignoreBlank?: boolean)
```

Sets the leading margin to reveal a small portion of the previous item. For the implementation example, see [Example 1: Setting the Navigation Dot Interaction and Page Turn Effect](../../../reference/apis-arkui/arkui-ts/ts-container-swiper.md#example-1-setting-the-navigation-indicator-interaction-and-page-turning-effect). This attribute takes effect only when the layout mode of the Swiper child components is stretch, which mainly includes two scenarios: 1. The **displayMode** attribute is set to **SwiperDisplayMode.STRETCH**; 2. The **displayCount** attribute is set to the number type.

When the main axis runs horizontally and either **nextMargin** or **prevMargin** is greater than the measured width of the child component, both margins are hidden.

When the main axis runs vertically and either **nextMargin** or **prevMargin** is greater than the measured height of the child component, both margins are hidden.

When using the **nextMargin**\/**prevMargin** API, do not set the [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) attribute for child components. Otherwise, the child node will not be stretched to the expected length along the main axis, and the margin will lose its effect.

> **NOTE:** 
> 
> This API cannot be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-SwiperAttribute-prevMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute--><!--Device-SwiperAttribute-prevMargin(value: Length, ignoreBlank?: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Front margin. Percentage is not supported.<br>Default value: 0<br>For details about the unit, see [Length](../arkts-apis/arkts-arkui-length-t.md). |
| ignoreBlank | boolean | No | Whether to hide the leading margin for the first page in non-loop scenarios.<br> **true**: Hide the leading margin, in which case, the left edge of the first page is aligned with that of the **Swiper** component's viewable area. <br>**false**: Show the leading margin, in which case, the first page has a **prevMargin**-specified gap from the **Swiper** component's left edge. <br>Default value: **false**. <br>**NOTE:** <br>On the first page, the values of **prevMargin** and **nextMargin** are added to create a right margin that allows the next page to be displayed partially.<br>**Since:** 12 |

## vertical

```TypeScript
vertical(value: boolean)
```

Sets whether vertical swiping is used.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

<!--Device-SwiperAttribute-vertical(value: boolean): SwiperAttribute--><!--Device-SwiperAttribute-vertical(value: boolean): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether vertical swiping is used. The value **true** means vertical swiping, and **false** means horizontal swiping.<br>Default value: **false**. |

## indicatorStyle

```TypeScript
indicatorStyle(value?: IndicatorStyle)
```

Sets the style of the navigation indicator.

> **NOTE:** 
> 
> Supported from API version 8 and deprecated since API version 10. You are advised to use
> [indicator(value: DotIndicator | DigitIndicator | boolean)](#indicator1)
> instead.

**Since:** 8

**Deprecated since:** 10

**Substitutes:** [indicator](#indicator1)(value: DotIndicator | DigitIndicator | boolean)

<!--Device-SwiperAttribute-indicatorStyle(value?: IndicatorStyle): SwiperAttribute--><!--Device-SwiperAttribute-indicatorStyle(value?: IndicatorStyle): SwiperAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [IndicatorStyle](arkts-arkui-swiper-comp-indicatorstyle-i.md) | No | Style of the navigation indicator. |
