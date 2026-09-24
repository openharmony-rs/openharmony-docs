# WaterFlow properties/events

```TypeScript
declare class WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>
```

In addition to universal attributes and [scrollable component common attributes](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#attributes), the following attributes are also supported.

In addition to universal events and [scrollable component common events](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#events), the following events are also supported.

**Inheritance/Implementation:** WaterFlowAttribute extends ScrollableCommonMethod<WaterFlowAttribute>

**Since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## cachedCount

```TypeScript
cachedCount(value: number)
```

Number of items to be preloaded.

This attribute takes effect only in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) with [virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled. **FlowItem** components that are outside the display and cache range will be released.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of water flow items to be preloaded (cached).<br>Default value: number of nodes visible on the screen, with the maximum value of 16<br>Value range: [0, +∞).<br>Values less than 0 are treated as **1**. |

<a id="cachedcount-1"></a>

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

Sets the number of flow items to be cached (preloaded) and specifies whether to display the preloaded nodes.

This attribute can be combined with the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attributes to display the preloaded nodes.

This parameter takes effect only when used with [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or the [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) component that has virtualScroll enabled. **FlowItem** elements outside the visible area and cache range will be released.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of water flow items to be preloaded (cached).<br>Default value: number of nodes visible on the screen, with the maximum value of 16<br>Value range: [0, +∞).<br>Values less than 0 are treated as **1**. |
| show | boolean | Yes | Whether to display the cached water flow items. If this parameter is set to **true**, the preloaded flow items are displayed. If this parameter is set to **false**, the preloaded flow items are not displayed.<br> Default value: **false**. |

## columnsGap

```TypeScript
columnsGap(value: Length)
```

Sets the gap between columns.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Gap between columns.<br>Default value: **0**<br>Value range: [0, +∞). A value less than 0 evaluates to the value **0**. |

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

Sets the number of columns in the layout. If this attribute is not set, one column is used by default.

For example, **'1fr 1fr 2fr'** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4.

You can use **columnsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of columns based on the specified column width **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number. For details, see [Example 2](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#example-2-implementing-automatic-column-count-calculation).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of columns in the layout.<br>Default value: **'1fr'** |

<a id="columnstemplate-1"></a>

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy)
```

Sets the number of columns in the layout. If this attribute is not set, one column is used by default.

When the value is of the string type, refer to [columnsTemplate(value: string)](#columnstemplate) for the usage.

When the value is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **WaterFlow** component.

For example, the **ItemFillPolicy.BREAKPOINT_DEFAULT** component displays two columns when the component width falls within the sm or smaller breakpoint range, three columns for the md breakpoint range, and five columns for the lg or larger breakpoint range, with each column being 1 fr.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of columns in the layout. |

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support scroll gestures. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the [Scroller](arkts-arkui-scroll-comp-scroller-c.md).<br>Default value: **true** |

## friction

```TypeScript
friction(value: number | Resource)
```

Sets the friction coefficient. It applies only to gestures in the scrolling area, and it affects only indirectly the scroll chaining during the inertial scrolling process.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.9** for wearable devices and **0.6** for non-wearable devices.<br>Since API version 11, the default value for non-wearable devices is **0.7**.<br>Since API version 12, the default value for non-wearable devices is **0.75**.<br>Value range: (0, + ∞).<br>If the value is less than or equal to 0, the default value is used. |

## itemConstraintSize

```TypeScript
itemConstraintSize(value: ConstraintSizeOptions)
```

Sets the size constraints of the child components during layout. For details about how to use this API, see [Example 1](../../../reference/apis-arkui/arkui-ts/ts-container-waterflow.md#example-1-using-a-basic-waterflow-component).

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ConstraintSizeOptions](../arkts-apis/arkts-arkui-constraintsizeoptions-i.md) | Yes | Size constraints of the child components during layout. If the value specified is less than **0**, this parameter does not take effect.<br>**NOTE:** <br>1. If both **itemConstraintSize** and the [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize) attribute of the **FlowItem** are set, the **minWidth** (or **minHeight**) will be the larger of the two values, and the **maxWidth** (or **maxHeight**) will be the smaller of the two values. The resulting values will then be used as the **constraintSize** for the **FlowItem**.<br>2. When only **itemConstraintSize** is set, it effectively applies a uniform size constraint to all child components in the **WaterFlow**.<br>3. The **itemConstraintSize** attribute, once converted to the **constraintSize** attribute of the **FlowItem** through the two methods mentioned above, follows the same rules for taking effect as the universal attribute [constraintSize](arkts-arkui-common-comp-commonmethod-c.md#constraintsize). |

## layoutDirection

```TypeScript
layoutDirection(value: FlexDirection)
```

Sets the main axis direction of the layout.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | Nested scrolling options. |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

Triggered when the **WaterFlow** content reaches the end position.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the **WaterFlow** content reaches the start position. |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

When this API is called back, the event parameter passes the scroll offset that is about to occur. The event processing function can calculate the actually required scroll offset based on the application scenario and return it as the return value. The **WaterFlow** component will then scroll according to this returned actual scroll offset.

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

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (first: number, last: number) =&gt; void | Yes | Callback function, triggered when the first or last item displayed in the waterflow changes."first": the index of the first item displayed in the waterflow,"last": the index of the last item displayed in the waterflow. |

## rowsGap

```TypeScript
rowsGap(value: Length)
```

Sets the gap between rows.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Gap between rows.<br>Default value: **0**<br>Value range: [0, +∞). A value less than 0 evaluates to the value **0**. |

## rowsTemplate

```TypeScript
rowsTemplate(value: string)
```

Sets the number of rows in the layout. If this attribute is not set, one row is used by default.

For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4.

You can use **rowsTemplate('repeat(auto-fill,track-size)')** to automatically calculate the number of rows based on the specified row height **track-size**. **repeat** and **auto-fill** are keywords. The units for **track-size** can be px, vp (default), %, or a valid number.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of rows in the layout.<br>Default value: **'1fr'** |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

Defines whether the **WaterFlow** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. If this attribute is not set, empty branch nodes are not supported. This attribute cannot be updated after being set. Therefore, you cannot switch between the behavior of supporting empty branches and the behavior of not supporting empty branches after setting this attribute.

> **NOTE:** 
> 
> When [WaterFlowSections](arkts-arkui-waterflow-comp-waterflowsections-c.md) is set using the [sections](arkts-arkui-waterflow-comp-waterflowoptions-i.md) parameter,
> or when the [SLIDING_WINDOW](arkts-arkui-waterflow-comp-waterflowlayoutmode-e.md) layout mode is set using the
> [layoutMode](arkts-arkui-waterflow-comp-waterflowoptions-i.md) parameter, the **FlowItem** after the empty branch is displayed regardless
> of the **supportEmptyBranchInLazyLoading** setting.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean &#124; undefined | Yes | Whether the current **WaterFlow** component supports the use of the [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) rendering syntax in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) to generate an empty branch node that contains no child component.<br>**true** indicates that the **FlowItem** after the empty branch is displayed; **false** indicates the opposite.<br>If the value is **undefined**, it is processed as **false**. |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

Sets whether to synchronously load all child components in the **WaterFlow** component.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to synchronously load all child components in the **WaterFlow** component.<br> **true**: synchronous loading; false: asynchronous loading<br>Default value: **true**<br>**NOTE:** <br>When this parameter is set to **false**, in the first display or [scrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex) jumps without animation, if the time consumed by the frame layout exceeds 50 ms, the child components that have not been laid out in the **WaterFlow** component are delayed to the next frame for layout. |
