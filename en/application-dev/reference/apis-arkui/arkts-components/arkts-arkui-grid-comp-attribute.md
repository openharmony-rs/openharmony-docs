# Grid properties/events

```TypeScript
declare class GridAttribute extends ScrollableCommonMethod<GridAttribute>
```

In addition to [universal attributes](arkts-arkui-common-comp.md) and [scrollable component common attributes](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#attributes), the following attributes are also supported.

In addition to [universal events](arkts-arkui-common-comp.md) and [scrollable component common events](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#events), the following events are also supported.

**Inheritance/Implementation:** GridAttribute extends ScrollableCommonMethod<GridAttribute>

**Since:** 7

<!--Device-unnamed-declare class GridAttribute extends ScrollableCommonMethod<GridAttribute>--><!--Device-unnamed-declare class GridAttribute extends ScrollableCommonMethod<GridAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignItems

```TypeScript
alignItems(alignment: Optional<GridItemAlignment>)
```

Sets the alignment mode of grid items in the grid. For details about the usage, see [Example 9](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-9-setting-grid-item-heights-based-on-the-tallest-item-in-the-current-row).

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-GridAttribute-alignItems(alignment: Optional<GridItemAlignment>): GridAttribute--><!--Device-GridAttribute-alignItems(alignment: Optional<GridItemAlignment>): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| alignment | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[GridItemAlignment](arkts-arkui-grid-comp-griditemalignment-e.md)&gt; | Yes | Alignment mode of grid items in the grid.<br>Default value: **GridItemAlignment.DEFAULT** |

## cachedCount

```TypeScript
cachedCount(value: number)
```

Sets the number of grid rows/columns to be preloaded on both sides along the main axis. This attribute takes effect only in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) with [virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled.<!--Del-->For details, see [Minimizing White Blocks During Swiping](../../../performance/arkts-performance-improvement-recommendation.md#minimizing-white-blocks-during-swiping). <!--DelEnd-->

After caching is set, **cachedCount** grid rows/columns are preloaded on both sides of the display area of the **Grid** component along the main axis. During vertical scrolling, **cachedCount** rows are preloaded on the top and bottom sides respectively. During horizontal scrolling, **cachedCount** columns are preloaded on the left and right sides respectively.

[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) with [virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled will release **GridItem** components that are outside the display and cache range.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-cachedCount(value: number): GridAttribute--><!--Device-GridAttribute-cachedCount(value: number): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of grid items to be cached (preloaded).<br>Default value: the number of rows visible on the screen for vertical scrolling, or the number of columns visible on the screen for horizontal scrolling. The maximum value is 16. <br>Value range: [0, +∞). <br>Values less than 0 are treated as **1**. <br>When **value** is updated using a state variable, the **Grid** component does not trigger a layout update. The number of cached nodes is updated only during the next layout. |

<a id="cachedcount-1"></a>

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

Sets the number of grid rows/columns to be preloaded on both sides along the main axis, and configures whether to display the preloaded nodes. This attribute takes effect only in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) with [virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll) enabled.

After caching is set, **cachedCount** grid rows/columns are preloaded on both sides of the display area of the **Grid** component along the main axis. During vertical scrolling, **cachedCount** rows are preloaded on the top and bottom sides respectively. During horizontal scrolling, **cachedCount** columns are preloaded on the left and right sides respectively. The preloaded nodes can be displayed together with the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attribute.

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

<!--Device-GridAttribute-cachedCount(count: number, show: boolean): GridAttribute--><!--Device-GridAttribute-cachedCount(count: number, show: boolean): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of grid items to be cached (preloaded).<br>Default value: the number of rows visible on the screen for vertical scrolling, or the number of columns visible on the screen for horizontal scrolling. The maximum value is 16. <br>Value range: [0, +∞). <br>Values less than 0 are treated as **1**. <br>When the count value is updated using the state variable, the **Grid** component does not trigger a layout update. The number of cached nodes is updated only during the next layout. |
| show | boolean | Yes | Whether to display the preloaded nodes. If this parameter is set to **true**, the preloaded **GridItem** is displayed. If this parameter is set to **false**, the preloaded **GridItem** is not displayed.<br> Default value: **false** |

## cellLength

```TypeScript
cellLength(value: number)
```

Sets the height per row or width per column.

> **NOTE:** 
> 
> This attribute takes effect only when neither **rowsTemplate** nor **columnsTemplate** is set.

When **layoutDirection** is **Row** or **RowReverse**, the value indicates the height per row.

When **layoutDirection** is **Column** or **ColumnReverse**, the value indicates the width per column.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-cellLength(value: number): GridAttribute--><!--Device-GridAttribute-cellLength(value: number): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Height of a row or width of a column.<br>Default value: when **layoutDirection** is **Row** or **RowReverse**, the height of the first **GridItem**; when **layoutDirection** is **Column** or **ColumnReverse**, the width of the first **GridItem**.<br>Unit: vp <br>Value range: (0, +∞). If the value is set to a value less than or equal to 0, the default value is used. |

## columnsGap

```TypeScript
columnsGap(value: Length)
```

Sets the gap between columns. A value less than 0 evaluates to the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-columnsGap(value: Length): GridAttribute--><!--Device-GridAttribute-columnsGap(value: Length): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Gap between columns.<br>Default value: **0**<br>Value range: [0, +∞). If a value less than 0 is set, the default value 0 is used. |

## columnsTemplate

```TypeScript
columnsTemplate(value: string)
```

Sets the number of columns, fixed column width, or minimum column width of the grid. If this attribute is not set, one column will be used.

For example, **&nbsp;'1fr&nbsp;1fr&nbsp;2fr'&nbsp;** indicates three columns, with the first column taking up 1/4 of the parent component's full width, the second column 1/4, and the third column 2/4.

**columnsTemplate('repeat(auto-fit, track-size)')**: The layout automatically calculates the number of columns and the actual column width, while adhering to the minimum column width specified with **track-size**.

**columnsTemplate('repeat(auto-fill, track-size)')**: The layout automatically calculates the number of columns based on the fixed column width specified with **track-size**.

**columnsTemplate('repeat(auto-stretch, track-size)')**: The layout uses **columnsGap** to define the minimum gap between columns and automatically calculates the number of columns and the actual gap size based on the fixed column width specified by **track-size**.

**repeat**, **auto-fit**, **auto-fill**, and **auto-stretch** are keywords. **track-size** indicates the column width, in the unit of px, vp (default), %, or any valid digit. The value must be greater than or equal to one valid column width.

In auto-fit and auto-stretch modes, only a valid column width value is supported for **track-size**. Additionally, in auto-stretch mode, **track-size** only supports units such as px, vp, and valid numbers, but does not support percentage (%). The auto-fill mode supports one or more valid column widths, for example, columnsTemplate('repeat(auto-fill, 20)') or columnsTemplate('repeat(auto-fill, 20 80px)').

For details about the effect, see [Example 8](arkts-arkui-grid-comp.md).

If this attribute is set to **'0fr'**, the column width is 0, and grid item in the column is not displayed. If this attribute is set to any other invalid value, the grid item is displayed as one column.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-columnsTemplate(value: string): GridAttribute--><!--Device-GridAttribute-columnsTemplate(value: string): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of columns or minimum column width of the grid. |

<a id="columnstemplate-1"></a>

## columnsTemplate

```TypeScript
columnsTemplate(value: string | ItemFillPolicy)
```

Number of columns in the current grid layout. If this attribute is not set, one column will be used.

When the value is of the string type, refer to [columnsTemplate(value: string)](#columnstemplate) for the usage.

When the value is of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **Grid** component.

For example, **ItemFillPolicy.BREAKPOINT_DEFAULT** displays two columns when the component width falls within the sm or smaller breakpoint range, three columns for the md breakpoint range, and five columns for the lg or larger breakpoint range, with each column being 1 fr.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-GridAttribute-columnsTemplate(value: string | ItemFillPolicy): GridAttribute--><!--Device-GridAttribute-columnsTemplate(value: string | ItemFillPolicy): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of columns in the current grid layout. When **value** is of the string type, it indicates a fixed number of columns or the **repeat** function form; when **value** is of the **ItemFillPolicy** type, the number of columns is automatically determined based on the breakpoint. |

## edgeEffect

```TypeScript
edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions)
```

Sets the effect used when the scroll boundary is reached.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions): GridAttribute--><!--Device-GridAttribute-edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.None** |
| options | [EdgeEffectOptions](arkts-arkui-common-comp-edgeeffectoptions-i.md) | No | Whether to enable the scroll effect when the component content is smaller than the component itself. The value **{ alwaysEnabled: true }** means to enable the scroll effect, and **{ alwaysEnabled: false }** means the opposite.<br>Default value: **{ alwaysEnabled: false }**<br>**Since:** 11 |

## editMode

```TypeScript
editMode(value: boolean)
```

Sets whether to enable edit mode. In edit mode, the user can drag the [grid items](arkts-arkui-griditem-comp.md) in the **Grid** component.

> **NOTE:** 
> 
> This attribute takes effect only when neither **rowsTemplate** nor **columnsTemplate** is set.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-editMode(value: boolean): GridAttribute--><!--Device-GridAttribute-editMode(value: boolean): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable edit mode. If this parameter is set to **true**, the **Grid** component is in edit mode. If this parameter is set to **false**, the **Grid** component is not in edit mode.<br>Default value: **false** |

## editModeOptions

```TypeScript
editModeOptions(options?: EditModeOptions)
```

Sets the options of the edit mode.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-GridAttribute-editModeOptions(options?: EditModeOptions): GridAttribute--><!--Device-GridAttribute-editModeOptions(options?: EditModeOptions): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditModeOptions](arkts-arkui-common-comp-editmodeoptions-i.md) | No | Edit mode options, used to configure behaviors such as the multi-select gathering animation, preview badge, multi-select style, and two-finger swipe multi-select in Grid edit mode. Pass this parameter when the preceding behaviors need to be adjusted; if it is not passed, each option uses the default value in the **EditModeOptions** object description. |

## enableEditMode

```TypeScript
enableEditMode(enabled: boolean | undefined)
```

Sets whether to enable the edit mode for the **Grid** component. After the edit mode is enabled, you can swipe to select multiple [GridItem](arkts-arkui-griditem-comp.md) components in the **Grid** component. If this API is not called, the edit mode is not enabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GridAttribute-enableEditMode(enabled: boolean | undefined): GridAttribute--><!--Device-GridAttribute-enableEditMode(enabled: boolean | undefined): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Whether to enable the editing mode. This parameter supports two-way binding with a variable through [!!](../../../ui/state-management/arkts-new-binding.md). When set to **true**, the editing mode is enabled and multiple items can be selected by swiping. When set to **false** or **undefined**, the editing mode is disabled and multiple items cannot be selected by swiping. |

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

<!--Device-GridAttribute-enableScrollInteraction(value: boolean): GridAttribute--><!--Device-GridAttribute-enableScrollInteraction(value: boolean): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support scroll gestures. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the [Scroller](arkts-arkui-scroll-comp-scroller-c.md). <br>Default value: **true** |

## focusWrapMode

```TypeScript
focusWrapMode(mode: Optional<FocusWrapMode>)
```

Sets the focus wrap mode for cross-axis arrow keys.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-GridAttribute-focusWrapMode(mode: Optional<FocusWrapMode>): GridAttribute--><!--Device-GridAttribute-focusWrapMode(mode: Optional<FocusWrapMode>): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[FocusWrapMode](../arkts-apis/arkts-arkui-focuswrapmode-e.md)&gt; | Yes | Focus wrap mode for cross-axis arrow keys.<br>Default value: **FocusWrapMode.DEFAULT** <br>**NOTE:** <br>Abnormal values are treated as the default value, meaning that cross-axis arrow keys cannot wrap. |

## friction

```TypeScript
friction(value: number | Resource)
```

Sets the friction coefficient. It takes effect when the scroll area is swiped, and affects only the inertial scrolling process. It has an indirect impact on the chained effect during inertial scrolling.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-friction(value: number | Resource): GridAttribute--><!--Device-GridAttribute-friction(value: number | Resource): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.9** for wearable devices and **0.6** for non-wearable devices <br>Since API version 11, the default value for non-wearable devices is **0.7**. <br>Since API version 12, the default value for non-wearable devices is **0.75**. <br>Value range: (0, +∞). If this parameter is set to a value less than or equal to 0, the default value is used. |

## layoutDirection

```TypeScript
layoutDirection(value: GridDirection)
```

Sets the main axis layout direction of the grid.

> **NOTE:** 
> 
> This attribute takes effect only when neither **rowsTemplate** nor **columnsTemplate** is set.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-layoutDirection(value: GridDirection): GridAttribute--><!--Device-GridAttribute-layoutDirection(value: GridDirection): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GridDirection](arkts-arkui-grid-comp-griddirection-e.md) | Yes | Main axis layout direction of the grid.<br>Default value: **GridDirection.Row** |

## maxCount

```TypeScript
maxCount(value: number)
```

Sets the maximum number of rows or columns that can be displayed. A value less than 1 evaluates to the default value.

> **NOTE:** 
> 
> This attribute takes effect only when neither **rowsTemplate** nor **columnsTemplate** is set.

When **layoutDirection** is **Row** or **RowReverse**, the value indicates the maximum number of columns that can be displayed.

When **layoutDirection** is **Column** or **ColumnReverse**, the value indicates the maximum number of rows that can be displayed.

If the value of **maxCount** is smaller than that of **minCount**, the default values of **maxCount** and **minCount** are used.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-maxCount(value: number): GridAttribute--><!--Device-GridAttribute-maxCount(value: number): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of rows or columns that can be displayed.<br>Default value: **Infinity**<br>Value range: [1, +∞). If the value is set to less than 1, the default value **Infinity** is used. |

## minCount

```TypeScript
minCount(value: number)
```

Sets the minimum number of rows or columns that can be displayed. A value less than 1 evaluates to the default value.

> **NOTE:** 
> 
> This attribute takes effect only when neither **rowsTemplate** nor **columnsTemplate** is set.

When **layoutDirection** is **Row** or **RowReverse**, the value indicates the minimum number of columns that can be displayed.

When **layoutDirection** is **Column** or **ColumnReverse**, the value indicates the minimum number of rows that can be displayed.

If the value of **minCount** is greater than that of **maxCount**, both **minCount** and **maxCount** are treated as using their default values.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-minCount(value: number): GridAttribute--><!--Device-GridAttribute-minCount(value: number): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Minimum number of rows or columns that can be displayed.<br>Default value: **1**<br> Value range: [1, +∞). If a value less than 1 is set, the default value **1** is used. |

## multiSelectable

```TypeScript
multiSelectable(value: boolean)
```

Sets whether to enable multiselect. After multiselect is enabled, you can use **GridItem**'s **selected** attributeand **onSelect** event to obtain the selection state of **GridItem**. Additionally, you can set the selected state style of **GridItem** using [Polymorphic Style](arkts-arkui-common-comp.md) (by default, **GridItem** has no selected state style).

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-multiSelectable(value: boolean): GridAttribute--><!--Device-GridAttribute-multiSelectable(value: boolean): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable multiselect.<br>Default value: **false** <br>**false**: Multiselect is disabled. **true**: Multiselect is enabled. |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

Sets the nested scrolling options. Sets the nested scrolling modes for both forward and backward directions to achieve scrolling linkage with the parent component. When the component content is smaller than the component itself and **options** of [edgeEffect](#edgeeffect) is set to **{ alwaysEnabled: false }**, the component's own swipe gesture will not be triggered, and the nested scroll property will not take effect. If its parent scrollable component has a swipe gesture, this swipe gesture will be triggered instead.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-nestedScroll(value: NestedScrollOptions): GridAttribute--><!--Device-GridAttribute-nestedScroll(value: NestedScrollOptions): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | Nested scroll options, used to set the nested scrolling linkage behavior between the **Grid** component and its parent component. |

## onEditModeChange

```TypeScript
onEditModeChange(callback: Callback<boolean> | undefined)
```

Triggered when the edit mode state of [enableEditMode](#enableeditmode) changes. This API uses an asynchronous callback to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GridAttribute-onEditModeChange(callback: Callback<boolean> | undefined): GridAttribute--><!--Device-GridAttribute-onEditModeChange(callback: Callback<boolean> | undefined): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; &#124; undefined | Yes | Callback invoked when the edit mode state changes. The callback parameter is of the boolean type. The value **true** indicates entering the edit mode, and **false** indicates exiting the edit mode.<br>If **undefined** is passed in, the callback is canceled. |

## onItemDragEnter

```TypeScript
onItemDragEnter(event: (event: ItemDragInfo) => void)
```

Triggered when a dragged item enters the range of a **GridItem**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onItemDragEnter(event: (event: ItemDragInfo) => void): GridAttribute--><!--Device-GridAttribute-onItemDragEnter(event: (event: ItemDragInfo) => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo) =&gt; void | Yes | Information about the drag point. |

## onItemDragLeave

```TypeScript
onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void)
```

Triggered when a dragged item leaves a **GridItem**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void): GridAttribute--><!--Device-GridAttribute-onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number) =&gt; void | Yes | Information about the drag point. |

## onItemDragMove

```TypeScript
onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void)
```

Triggered when a dragged item moves within the range of a **GridItem**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void): GridAttribute--><!--Device-GridAttribute-onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number) =&gt; void | Yes | Information about the drag point. |

## onItemDragStart

```TypeScript
onItemDragStart(event: OnItemDragStartCallback)
```

Triggered when dragging of a **GridItem** starts.

This event is triggered when the user long presses a grid item.

Drag gesture recognition is also initiated by a long press, and the event processing mechanism prioritizes child component events. Therefore, when the grid item is bound to the [LongPressGesture](arkts-arkui-tapgesture-comp-longpressgestureinterface-i.md), it cannot be dragged. In light of this, if both long press and drag operations are required on the grid item, you can use the universal drag event.

The dragged and lifted **GridItem** can move within the app window. To restrict the movement range, you can implement it through a custom gesture. For details, see [Example 16: Customizing the Drag Effect for GridItem](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-16-customizing-the-drag-effect-for-griditem).

Automatic scrolling when dragging to the edge of the **Grid** is not supported. You can use the universal drag to implement it. For details, see [Example 17: Dragging Grid Items with Drag Events](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-17-dragging-grid-items-with-drag-events). Since API version 26.0.0, you can use the [onMove](arkts-arkui-common-comp-dynamicnode-c.md#onmove) API of [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) to implement this effect. For details, see [Example 22 (Dragging with OnMove)](arkts-arkui-grid-comp.md). It also supports dragging of **GridItem** that spans rows and columns, but note that the **Grid** must be scrollable.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onItemDragStart(event: OnItemDragStartCallback): GridAttribute--><!--Device-GridAttribute-onItemDragStart(event: OnItemDragStartCallback): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnItemDragStartCallback](arkts-arkui-common-comp-onitemdragstartcallback-t.md) | Yes | Callback triggered when the drag of a **GridItem** starts. <br>In API version 22 and earlier versions, the type of this parameter is **(event: ItemDragInfo, itemIndex: number) =&gt; (() =&gt; any) &#124; void**. For the meanings of the **event** and **itemIndex** parameters, see [OnItemDragStartCallback](arkts-arkui-common-comp-onitemdragstartcallback-t.md).<br>**Since:** 23 |

## onItemDrop

```TypeScript
onItemDrop(
    event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void,
  )
```

The **GridItem** bound with this event can serve as a drop target. This event is triggered when the **GridItem** stops being dragged.

When the drop position is within the **GridItem**, **isSuccess** returns **true**; when it is outside the **GridItem**, **isSuccess** returns **false**.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onItemDrop(    event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void,  ): GridAttribute--><!--Device-GridAttribute-onItemDrop(    event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void,  ): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) =&gt; void | Yes | Information about the drag point. |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

Triggered when the grid reaches the end position. It is triggered when the grid content does not fill one screen and the end of the last child component is within the **Grid**.

When the edge effect of the **Grid** is a spring effect, this event is triggered once when the swipe passes the end position and once again when the rebound returns to the end position.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onReachEnd(event: () => void): GridAttribute--><!--Device-GridAttribute-onReachEnd(event: () => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the grid reaches the end position. |

## onReachStart

```TypeScript
onReachStart(event: () => void)
```

Triggered when the grid reaches the start position.

This event is triggered once when the **Grid** is initialized and once when the **Grid** scrolls to the start position. When the edge effect of the **Grid** is a spring effect, this event is triggered once when the swipe passes the start position and once again when the rebound returns to the start position.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onReachStart(event: () => void): GridAttribute--><!--Device-GridAttribute-onReachStart(event: () => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the grid reaches the start position. |

## onScrollBarUpdate

```TypeScript
onScrollBarUpdate(event: (index: number, offset: number) => ComputedBarAttribute)
```

Triggered at the end of each frame layout in the grid. You can use the callback to set the position and length of the scrollbar.

This API is intended solely for setting the scroll position of the grid. Avoid implementing service logic within this API.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onScrollBarUpdate(event: (index: number, offset: number) => ComputedBarAttribute): GridAttribute--><!--Device-GridAttribute-onScrollBarUpdate(event: (index: number, offset: number) => ComputedBarAttribute): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (index: number, offset: number) =&gt; ComputedBarAttribute | Yes | callback of grid scroll, index: Index of the first item of the grid. offset: Offset of the displayed first item relative to the start position of the grid, in vp. return ComputedBarAttribute: Position and length of the scrollbar. |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

When this API is called back, the event parameter passes the scroll offset that is about to occur. The event processing function can calculate the actually required scroll offset based on the application scenario and return it as the return value. The grid will then scroll according to this returned actual scroll offset.

This event is triggered when either of the following conditions is met:

1. Scrolling is initiated by user interaction (for example, finger swipe, keyboard, or mouse operation).
2. The **Grid** component scrolls by inertia.
3. Call the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) API to trigger scrolling.

This event is not triggered in the following scenarios:

1. A scroll control API other than [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) is called.
2. The out-of-bounds bounce effect is active.
3. The scrollbar is dragged.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): GridAttribute--><!--Device-GridAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-scroll-comp-onscrollframebegincallback-t.md) | Yes | Callback triggered when each frame scrolling starts.<br>**Since:** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (first: number, last: number) => void)
```

Triggered when the first or last item displayed in the grid changes, that is, when the index of either the first or last item changes. It is triggered once when the grid is initialized.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onScrollIndex(event: (first: number, last: number) => void): GridAttribute--><!--Device-GridAttribute-onScrollIndex(event: (first: number, last: number) => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (first: number, last: number) =&gt; void | Yes | of grid scroll, first is the index of the first item displayed in the grid, last is the index of the last item displayed in the grid. |

## onScrollStart

```TypeScript
onScrollStart(event: () => void)
```

Triggered when the grid starts scrolling initiated by the user's finger dragging the grid or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) starts.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onScrollStart(event: () => void): GridAttribute--><!--Device-GridAttribute-onScrollStart(event: () => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the grid starts scrolling. |

## onScrollStop

```TypeScript
onScrollStop(event: () => void)
```

Triggered when the grid stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) stops.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onScrollStop(event: () => void): GridAttribute--><!--Device-GridAttribute-onScrollStop(event: () => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback when the grid stops scrolling. |

## rowsGap

```TypeScript
rowsGap(value: Length)
```

Sets the gap between rows. A value less than 0 evaluates to the default value.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-rowsGap(value: Length): GridAttribute--><!--Device-GridAttribute-rowsGap(value: Length): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Length](../arkts-apis/arkts-arkui-length-t.md) | Yes | Gap between rows.<br>Default value: 0<br>Value range: [0, +∞). If a value less than 0 is set, the default value 0 is used. |

## rowsTemplate

```TypeScript
rowsTemplate(value: string)
```

Sets the number of rows, fixed row height, or minimum row height of the grid. If this attribute is not set, one row will be used.

For example, **'1fr 1fr 2fr'** indicates three rows, with the first row taking up 1/4 of the parent component's full height, the second row 1/4, and the third row 2/4.

**rowsTemplate('repeat(auto-fit, track-size)')**: The layout automatically calculates the number of rows and the actual row height, while adhering to the minimum row height specified with **track-size**.

**rowsTemplate('repeat(auto-fill, track-size)')**: The layout automatically calculates the number of rows based on the fixed row height specified with **track-size**.

**rowsTemplate('repeat(auto-stretch, track-size)')**: The layout uses **rowsGap** to define the minimum gap between rows and automatically calculates the number of rows and the actual gap size based on the fixed row height specified with **track-size**.

**repeat**, **auto-fit**, **auto-fill**, and **auto-stretch** are keywords. **track-size** indicates the row height, in the unit of px, vp (default), %, or any valid digit. The value must be greater than or equal to one valid row height.

In auto-fit and auto-stretch modes, only a valid row height value is supported for **track-size**. Additionally, in auto-stretch mode, **track-size** only supports units such as px, vp, and valid numbers, but does not support percentage (%). The auto-fill mode supports one or more valid row heights, for example, rowsTemplate('repeat(auto- fill, 20)') or rowsTemplate('repeat(auto-fill, 20 80px)').

If this attribute is set to **'0fr'**, the row height is 0, and grid item in the row is not displayed. If this attribute is set to any other invalid value, the grid item is displayed as one row.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-rowsTemplate(value: string): GridAttribute--><!--Device-GridAttribute-rowsTemplate(value: string): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | string | Yes | Number of rows or minimum row height of the grid. |

## scrollBar

```TypeScript
scrollBar(value: BarState)
```

Sets the scrollbar state.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-scrollBar(value: BarState): GridAttribute--><!--Device-GridAttribute-scrollBar(value: BarState): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Scrollbar state.<br>Default value: **BarState.Auto** <br>**NOTE:** <br>In API version 9 and earlier versions, the default value is **BarState.Off**. Since API version 10, the default value is **BarState.Auto**. |

## scrollBarColor

```TypeScript
scrollBarColor(value: Color | number | string)
```

Sets the scrollbar color.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-scrollBarColor(value: Color | number | string): GridAttribute--><!--Device-GridAttribute-scrollBarColor(value: Color | number | string): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string | Yes | Scrollbar color.<br>Default value: **'#182431'** (40% opacity) <br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. <br>A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**. |

<a id="scrollbarcolor-1"></a>

## scrollBarColor

```TypeScript
scrollBarColor(color: Color | number | string | Resource)
```

Sets the scrollbar color. Compared with [scrollBarColor](#scrollbarcolor), the parameter name is changed to **color** and the Resource type is supported.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-GridAttribute-scrollBarColor(color: Color | number | string | Resource): GridAttribute--><!--Device-GridAttribute-scrollBarColor(color: Color | number | string | Resource): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| color | [Color](../arkts-apis/arkts-arkui-color-e.md) &#124; number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar color.<br>Default value: **'#182431'** (40% opacity) <br>A number value indicates a HEX color in RGB or ARGB format, for example, **0xffffff**. A string value indicates a color in RGB or ARGB format, for example, **'#ffffff'**. |

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string)
```

Sets the width of the scrollbar. Percentage values are not supported. After the width is set, the scrollbar width in both the normal state and the pressed state is the set value. If the scrollbar width exceeds the visible size of the **Grid** component along the main axis, the scrollbar width changes to the default value of 4 vp.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-scrollBarWidth(value: number | string): GridAttribute--><!--Device-GridAttribute-scrollBarWidth(value: number | string): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string | Yes | Width of the scrollbar.<br>Default value: **4**<br>Unit: vp<br>Value range: [0, +∞). If the value is less than 0, the default value is used. If the value is 0, the scrollbar is not displayed. |

<a id="scrollbarwidth-1"></a>

## scrollBarWidth

```TypeScript
scrollBarWidth(value: number | string | Resource)
```

Sets the width of the scrollbar. Percentage values are not supported. After the width is set, the scrollbar width in both the normal state and the pressed state is the set value. If the scrollbar width exceeds the visible size of the **Grid** component along the main axis, the scrollbar width changes to the default value of 4 vp. Resource type is supported.

If this attribute is not set, the scrollbar width is 4 vp.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-GridAttribute-scrollBarWidth(value: number | string | Resource): GridAttribute--><!--Device-GridAttribute-scrollBarWidth(value: number | string | Resource): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; string &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Scrollbar width.<br>Unit: vp <br>The value range is [0, +∞). If this parameter is set to a value less than 0, **4vp** is used. The value **0** means not to show the scrollbar. |

## supportAnimation

```TypeScript
supportAnimation(value: boolean)
```

Sets whether to enable animation. Currently, the grid item drag animation is supported. Animation is supported only in scrolling mode (only **rowsTemplate** or **columnsTemplate** is set).

Drag animations are only supported in grids with fixed size rules; scenarios involving spanning across rows or columns are not supported.

For details about the **supportAnimation** animation effect, see [Example 5: Implementing Dragging in a Grid](../../../reference/apis-arkui/arkui-ts/ts-container-grid.md#example-5-implementing-dragging-in-a-grid). For other animation effects, customize the drag effect.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-supportAnimation(value: boolean): GridAttribute--><!--Device-GridAttribute-supportAnimation(value: boolean): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable animation. If this parameter is set to **true**, the drag animation of **GridItem** is supported. If this parameter is set to **false**, the drag animation of **GridItem** is not supported.<br>Default value: **false** |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

Sets whether the current **Grid** component supports the use of the if/else rendering syntax in **LazyForEach** or **Repeat** to generate an empty branch node that contains no child component. If this attribute is not set, empty branch nodes are not supported. This attribute cannot be updated after being set. Therefore, you cannot switch between the behavior of supporting empty branches and the behavior of not supporting empty branches after setting this attribute.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-GridAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): GridAttribute--><!--Device-GridAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean &#124; undefined | Yes | Whether the current **Grid** component supports the use of the [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) rendering syntax in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) to generate an empty branch node that contains no child component.<br>**true**: yes; **false**: no<br>If the value is **undefined**, it is processed as **false**. |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

Sets whether to synchronously load all child components in the grid.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-GridAttribute-syncLoad(enable: boolean): GridAttribute--><!--Device-GridAttribute-syncLoad(enable: boolean): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to synchronously load all child components in the grid.<br> **true**: yes; **false**: no Default value: **true** <br> **NOTE:** <br>When this parameter is set to **false**, in the first display or **scrollToIndex** jumps without animation, if the time consumed by the frame layout exceeds 50 ms, the child components that have not been laid out in the grid are delayed to the next frame for layout. |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)
```

Called When sliding the grid.

**Since:** 10

**Deprecated since:** 12

**Substitutes:** onDidScroll

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-GridAttribute-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): GridAttribute--><!--Device-GridAttribute-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): GridAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) =&gt; void | Yes | callback of grid scroll, scrollOffset: Offset relative to the previous frame. The offset is positive when the **Grid** component is scrolled up and negative when it is scrolled down.<br>Unit: vp scrollState: Current scroll state. |
