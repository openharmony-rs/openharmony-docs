# WaterFlow properties/events

```TypeScript
declare class WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>
```

In addition to [universal attributes](arkts-arkui-common-comp.md) and [universal attributes of scrollable components](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#attributes), the following attributes are supported:

In addition to [universal events](arkts-arkui-common-comp.md) and [scrollable component common events](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#events), the following events are also supported.

**Inheritance/Implementation:** WaterFlowAttribute extends ScrollableCommonMethod&lt;WaterFlowAttribute&gt;

**Since:** 9

<!--Device-unnamed-declare class WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>--><!--Device-unnamed-declare class WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

<a id="cachedcount1"></a>

## cachedCount

```TypeScript
cachedCount(value: number)
```

Number of items to be preloaded.

This attribute takes effect only in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) with [virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled. **FlowItem** components that are outside the display and cache range will be released.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-WaterFlowAttribute-cachedCount(value: number): WaterFlowAttribute--><!--Device-WaterFlowAttribute-cachedCount(value: number): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of water flow items to be preloaded (cached).<br>Default value: number of nodes visible on the screen, with the maximum value of 16 <br>Value range: [0, +∞). <br>Values less than 0 are treated as **1**. |

<a id="cachedcount2"></a>

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

Sets the number of flow items to be cached (preloaded) and specifies whether to display the preloaded nodes.

This attribute can be combined with the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip1) or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attributes to display the preloaded nodes.

This parameter takes effect only when used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or the [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) component that has virtualScroll enabled. **FlowItem** elements outside the visible area and cache range will be released.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-WaterFlowAttribute-cachedCount(count: number, show: boolean): WaterFlowAttribute--><!--Device-WaterFlowAttribute-cachedCount(count: number, show: boolean): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of water flow items to be preloaded (cached).<br>Default value: number of nodes visible on the screen, with the maximum value of 16 <br>Value range: [0, +∞). <br>Values less than 0 are treated as **1**. |
| show | boolean | Yes | Whether to display the cached water flow items. If this parameter is set to **true**, the preloaded flow items are displayed. If this parameter is set to **false**, the preloaded flow items are not displayed.<br> Default value: **false**. |

## columnsGap

```TypeScript
columnsGap(value: Length)
```

Sets the gap between columns. When group layout is used, each group can set the column gap separately through **SectionOptions.columnsGap** to override this value.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-columnsGap(value: Length): WaterFlowAttribute--><!--Device-WaterFlowAttribute-columnsGap(value: Length): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Gap between columns.<br>Default value: **0**<br>Unit: vp<br>Value range: [0, +∞). Values less than 0 are treated as 0. |

<a id="columnstemplate1"></a>

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

Sets the number of columns in the layout of the current **WaterFlow** component. If this attribute is not set, one column is used by default. When [layoutDirection](#layoutdirection) is set to horizontal layout (**FlexDirection.Row** or **FlexDirection.RowReverse**), **columnsTemplate** does not take effect, and the layout is controlled by [rowsTemplate](#rowstemplate). When [sections](arkts-arkui-waterflow-comp-waterflowoptions-i.md) is used for group mixing layout, this attribute is ignored.

For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4.

You can use **columnsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of columns based on the specified column width **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. For details, see [Example 2](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#example-2-implementing-automatic-column-count-calculation).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-columnsTemplate(value: string): WaterFlowAttribute--><!--Device-WaterFlowAttribute-columnsTemplate(value: string): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of columns in the layout.<br>Default value: **'1fr'** |

<a id="columnstemplate2"></a>

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy)
```

Sets the number of columns in the layout of the current **WaterFlow** component. If this attribute is not set, one column is used by default. When [layoutDirection](#layoutdirection) is set to horizontal layout (**FlexDirection.Row** or **FlexDirection.RowReverse**), **columnsTemplate** does not take effect, and the layout is controlled by [rowsTemplate](#rowstemplate). When [sections](arkts-arkui-waterflow-comp-waterflowoptions-i.md) is used for group mixing layout, this attribute is ignored.

When the value is of the string type, refer to [columnsTemplate(value: string)](#columnstemplate1) for the usage.

When the value is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **WaterFlow** component.

For example, when the **fillType** attribute of **ItemFillPolicy** is set to **PresetFillType.BREAKPOINT_DEFAULT**, two columns are displayed when the component width falls within the **sm** and smaller breakpoint ranges, three columns are displayed within the **md** breakpoint range, and five columns are displayed within the **lg** and larger breakpoint ranges, with each column being 1fr.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-WaterFlowAttribute-columnsTemplate(value: string | ItemFillPolicy): WaterFlowAttribute--><!--Device-WaterFlowAttribute-columnsTemplate(value: string | ItemFillPolicy): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of columns in the current **WaterFlow** component layout. When **value** is of the **ItemFillPolicy** type, the number of columns is automatically determined based on the breakpoint type corresponding to the **WaterFlow** component width. |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

Sets whether to support the scrolling gesture.

> **NOTE:** 
> 
> The component cannot be scrolled through mouse press-and-drag operations.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-enableScrollInteraction(value: boolean): WaterFlowAttribute--><!--Device-WaterFlowAttribute-enableScrollInteraction(value: boolean): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support scroll gestures. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the [Scroller](arkts-arkui-scroll-comp-scroller-c.md). <br>Default value: **true** |

## friction

```TypeScript
friction(value: number | Resource)
```

Sets the friction coefficient. It takes effect when the scroll area is manually scrolled, affects only the inertial scrolling process, and has an indirect effect on the linkage effect of inertia being transferred to the parent component during nested scrolling. It is suitable for scenarios where the sliding inertia effect of the waterfall flow needs to be adjusted.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-friction(value: number | Resource): WaterFlowAttribute--><!--Device-WaterFlowAttribute-friction(value: number | Resource): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.9** for wearable devices and **0.6** for non-wearable devices. <br>Since API version 11, the default value for non-wearable devices is **0.7**. <br>Since API version 12, the default value for non-wearable devices is **0.75**. <br>Value range: (0, +∞). <br>If the value is less than or equal to 0, the default value is used. |

## itemConstraintSize

```TypeScript
itemConstraintSize(value: ConstraintSizeOptions)
```

Sets the constraint size, which is used to limit the size range of child components during layout. For details about how to use this API, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#example-1-using-a-basic-waterflow-component).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-itemConstraintSize(value: ConstraintSizeOptions): WaterFlowAttribute--><!--Device-WaterFlowAttribute-itemConstraintSize(value: ConstraintSizeOptions): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Constraint size. If a value less than 0 is set, the parameter does not take effect. <br>**NOTE:** <br>1. When both **itemConstraintSize** and the [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) attribute of **FlowItem** are set, the maximum value is used for **minWidth** or **minHeight**, and the minimum value is used for **maxWidth** or **maxHeight**. The adjusted values are then processed as the **constraintSize** of **FlowItem**. <br>2. When only **itemConstraintSize** is set, it is equivalent to setting the same **constraintSize** for all child components of **WaterFlow**. <br>3. After **itemConstraintSize** is converted to the **constraintSize** of **FlowItem** in either of the two ways above, the effective rules are the same as those of the universal attribute [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize). |

## layoutDirection

```TypeScript
layoutDirection(value: FlexDirection)
```

Sets the main axis direction of the layout.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-layoutDirection(value: FlexDirection): WaterFlowAttribute--><!--Device-WaterFlowAttribute-layoutDirection(value: FlexDirection): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [FlexDirection](../arkts-apis/arkts-arkui-flexdirection-e.md) | Yes | Main axis direction of the layout.<br>Default value: **FlexDirection.Column** |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

Sets the nested scrolling mode in the forward and backward directions to implement scrolling linkage with the parent component. For details, see [Example 3: Implementing Nested Scrolling (Method 2)](../../../reference/apis-arkui/arkui-ts/ts-container-scroll.md#example-3-implementing-nested-scrolling-method-2).

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-nestedScroll(value: NestedScrollOptions): WaterFlowAttribute--><!--Device-WaterFlowAttribute-nestedScroll(value: NestedScrollOptions): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | Nested scroll options, used to set the nested scrolling mode in both forward and backward directions to implement scrolling linkage with the parent component. |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

Triggered when the **WaterFlow** content reaches the end position.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-onReachEnd(event: () => void): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onReachEnd(event: () => void): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the **WaterFlow** content reaches the end position. |

## onReachStart

```TypeScript
onReachStart(event: () => void)
```

Triggered when the **WaterFlow** content reaches the start position.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-onReachStart(event: () => void): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onReachStart(event: () => void): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the **WaterFlow** content reaches the start position. |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

When this API is called back, the event parameter carries the amount of scrolling that is about to occur. The event handler can calculate the actual amount of scrolling required based on the app scenario and return that value. The waterfall flow scrolls according to the returned actual amount. It is suitable for scenarios where custom scrolling behavior is required, such as adjusting the amount of scrolling per frame proportionally or blocking the scrolling of the current frame under specific conditions.

This event is triggered when either of the following conditions is met:

1. Scrolling is initiated by user interaction (for example, finger swipe, keyboard, or mouse operation).
2. The **WaterFlow** component scrolls by inertia.
3. Scrolling is triggered by calling the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) API.

This event is not triggered in the following scenarios:

1. A scroll control API other than [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) is called.
2. The out-of-bounds bounce effect is active.
3. The scrollbar is dragged.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-scroll-comp-onscrollframebegincallback-t.md) | Yes | Callback triggered when each frame scrolling starts.<br>**Since:** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (first: number, last: number) => void)
```

Triggered when the first or last item displayed in the component changes. It is triggered once when the component is initialized.

This event is triggered when either of the preceding indexes changes.

> **NOTE:** 
> 
> This API can be called in [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 20.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-onScrollIndex(event: (first: number, last: number) => void): WaterFlowAttribute--><!--Device-WaterFlowAttribute-onScrollIndex(event: (first: number, last: number) => void): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (first: number, last: number) =&gt; void | Yes | Callback function, triggered when the first or last item displayed in the waterflow changes."first": the index of the first item displayed in the waterflow,"last": the index of the last item displayed in the waterflow. |

## rowsGap

```TypeScript
rowsGap(value: Length)
```

Sets the gap between rows. When group layout is used, each group can set the row gap separately through **SectionOptions.rowsGap** to override this value.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-rowsGap(value: Length): WaterFlowAttribute--><!--Device-WaterFlowAttribute-rowsGap(value: Length): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Gap between rows.<br>Default value: 0<br>Unit: vp<br>Value range: [0, +∞). Values less than 0 are treated as 0. |

## rowsTemplate

```TypeScript
rowsTemplate(value: string)
```

Sets the number of rows in the layout of the current **WaterFlow** component. If this attribute is not set, one row is used by default. When [layoutDirection](#layoutdirection) is set to vertical layout (**FlexDirection.Column** or **FlexDirection.ColumnReverse**) or is not set, **rowsTemplate** does not take effect, and the layout is controlled by [columnsTemplate](#columnstemplate1). When [sections](arkts-arkui-waterflow-comp-waterflowoptions-i.md) is used for group mixing layout, this attribute is ignored.

For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4.

You can use **rowsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-WaterFlowAttribute-rowsTemplate(value: string): WaterFlowAttribute--><!--Device-WaterFlowAttribute-rowsTemplate(value: string): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of rows in the layout.<br>Default value: **'1fr'** |

## scrollPlaceholder

```TypeScript
scrollPlaceholder(provider?: PlaceholderProvider)
```

Sets a scroll placeholder provider for the **WaterFlow** component. When the framework predicts that creating the next item within the remaining frame budget would overrun the frame, it first displays a placeholder for that item and creates the real item across frames on the UI thread.

The provider returns the placeholder description of an item: **id** refers to a template registered through [getPlaceholderRegister()](../arkts-apis/arkts-arkui-arkui-uicontext-uicontext-c.md#getplaceholderregister).register and **size** is a layout suggestion. If the provider returns **undefined**, or the returned **id** is missing or not registered, the system default placeholder is used and scrolling is not interrupted.

<br>**NOTE:** <br>
1. This attribute is opt-in: if it is not set, the **WaterFlow** component keeps the current
behavior, including the semantics of **syncLoad**.
2. The placeholder template must be a global, parameterless  
**@Builder({ isPlaceholder: true })** function that performs read-only static rendering.
3. After the real item has been created, it is re-laid out under the normal layout constraints of
the water flow item and replaces the placeholder, keeping the scroll anchor.

**Since:** 26.2.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.2.0.

<!--Device-WaterFlowAttribute-scrollPlaceholder(provider?: PlaceholderProvider): WaterFlowAttribute--><!--Device-WaterFlowAttribute-scrollPlaceholder(provider?: PlaceholderProvider): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| provider | [PlaceholderProvider](arkts-arkui-waterflow-comp-placeholderprovider-t.md) | No | Placeholder provider of the item at the given index. |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

Defines whether the **WaterFlow** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. If this attribute is not set, empty branch nodes are not supported. This attribute cannot be updated after being set. Therefore, you cannot switch between the behavior of supporting empty branches and the behavior of not supporting empty branches after setting this attribute.

> **NOTE:** 
> 
> When [WaterFlowSections](arkts-arkui-waterflow-comp-waterflowoptions-i.md) groups are set through the [sections](arkts-arkui-waterflow-comp-waterflowsections-c.md)
> parameter, or the [SLIDING_WINDOW](arkts-arkui-waterflow-comp-waterflowoptions-i.md) layout mode is set through
> [layoutMode](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md), the **FlowItem** components after an empty branch are displayed
> regardless of the value of **supportEmptyBranchInLazyLoading** or whether it is set.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-WaterFlowAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): WaterFlowAttribute--><!--Device-WaterFlowAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean &#124; undefined | Yes | Whether the current **WaterFlow** component supports using the [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) rendering control syntax in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) to generate an empty branch node that contains no child components. <br>The value **true** indicates that the FlowItem after the empty branch is displayed, and **false** indicates that it is not displayed. <br>If the value is undefined, it is processed as **false**. |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

Sets whether to synchronously load all child components in the **WaterFlow** component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-WaterFlowAttribute-syncLoad(enable: boolean): WaterFlowAttribute--><!--Device-WaterFlowAttribute-syncLoad(enable: boolean): WaterFlowAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to synchronously load all child components in the **WaterFlow** component. <br>**true**: synchronous loading; false: asynchronous loading <br>Default value: **true** <br>**NOTE:** <br>When this parameter is set to **false**, in the first display or [scrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex) jumps without animation, if the time consumed by the frame layout exceeds 50 ms, the child components that have not been laid out in the **WaterFlow** component are delayed to the next frame for layout. |
