# List properties/events

```TypeScript
declare class ListAttribute extends ScrollableCommonMethod<ListAttribute>
```

In addition to [universal attributes](arkts-arkui-common-comp.md) and [scrollable component common attributes](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#attributes), the following attributes are also supported.

In addition to [universal events](arkts-arkui-common-comp.md) and [scrollable component common events](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#events), the following events are also supported.

**Inheritance/Implementation:** ListAttribute extends ScrollableCommonMethod<ListAttribute>

**Since:** 7

<!--Device-unnamed-declare class ListAttribute extends ScrollableCommonMethod<ListAttribute>--><!--Device-unnamed-declare class ListAttribute extends ScrollableCommonMethod<ListAttribute>-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignListItem

```TypeScript
alignListItem(value: ListItemAlign)
```

Sets the layout mode of list items along the cross axis when the cross-axis width of the list is greater than the value calculated by the following formula: cross-axis width of list items × lanes + (lanes – 1) × gutter.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-alignListItem(value: ListItemAlign): ListAttribute--><!--Device-ListAttribute-alignListItem(value: ListItemAlign): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListItemAlign](arkts-arkui-list-comp-listitemalign-e.md) | Yes | Alignment mode of list items along the cross axis.<br>Default value: **ListItemAlign.Start** |

## backPressBehavior

```TypeScript
backPressBehavior(behavior: ListBackPressBehavior | undefined)
```

Sets the system back button behavior of the **List** component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ListAttribute-backPressBehavior(behavior: ListBackPressBehavior | undefined): ListAttribute--><!--Device-ListAttribute-backPressBehavior(behavior: ListBackPressBehavior | undefined): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| behavior | [ListBackPressBehavior](arkts-arkui-list-comp-listbackpressbehavior-i.md) &#124; undefined | Yes | System back button behavior of the **List** component. Currently, you can use the [ListBackPressBehavior](arkts-arkui-list-comp-listbackpressbehavior-i.md) parameter to configure whether to collapse the expanded swipe-out component of a **ListItem** when the system back button takes effect. <br>If this parameter is set to **undefined**, the default behavior is restored. That is, when the system back button takes effect, the expanded swipe-out component of the **ListItem** is collapsed. |

## cachedCount

```TypeScript
cachedCount(value: number)
```

Sets the number of **ListItem** or **ListItemGroup** components to be preloaded (cached). In a lazy loading scenario, only the **cachedCount** rows of **ListItem** components above and below the visible area of the **List** component is preloaded. In a non-lazy loading scenario, all items are loaded at once. For both lazy and non-lazy loading, only the content within the list display area plus the content equivalent to **cachedCount** outside the display area is laid out. <!--Del-->For details, see [Minimizing White Blocks During Swiping](../../../performance/arkts-performance-improvement-recommendation.md#minimizing-white-blocks-during-swiping). <!--DelEnd-->

When **cachedCount** is set for the list, the system preloads and lays out the **cachedCount**-specified number of rows of list items both above and below the currently visible area of the list. When calculating the number of rows for list items, the system takes into account the number of rows from the list items within a list item group. If a list item group does not contain any list items, then the entire list item group is counted as one row.

When **LazyForEach** is nested under **List**, and **ListItemGroup** is nested under **LazyForEach**, **LazyForEach** creates **cachedCount**-specified number of **ListItemGroup** components both above and below the display area of **List**.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-cachedCount(value: number): ListAttribute--><!--Device-ListAttribute-cachedCount(value: number): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of list items or list item groups to be preloaded (cached).<br>Default value: number of nodes visible on the screen, with the maximum value of 16 <br>Value range: [0, +∞). <br>Values less than 0 are treated as **1**. |

<a id="cachedcount-1"></a>

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

Sets the number of rows to be preloaded for the list and specifies whether to display the preloaded nodes. In the lazy loading scenario, **cachedCount** rows are preloaded both above and below the display area of **List**. In the non-lazy loading scenario, all child components are loaded.

After **cachedCount** is set for the list, **cachedCount** rows are preloaded and laid out both above and below the display area. When calculating the number of preloaded rows, the number of **ListItem** rows inside a **ListItemGroup** is counted. If a **ListItemGroup** contains no **ListItem**, the entire **ListItemGroup** is counted as one row. The preloaded nodes can be displayed together with the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attribute.

> **NOTE:** 
> 
> You are advised to set cachedCount to n/2 (n indicates the number of list items displayed on one screen). You
> also need to consider other factors to balance the experience and memory usage. For best practices, see
> [Cache List Items](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list#section11667144010222).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**Widget capability:** This API can be used in ArkTS widgets since API version 14.

<!--Device-ListAttribute-cachedCount(count: number, show: boolean): ListAttribute--><!--Device-ListAttribute-cachedCount(count: number, show: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of preloaded rows in the list.<br>Default value: determined by the number of nodes displayed on the screen, with a maximum of 16. <br>Value range: [0, +∞). If the value is less than 0, it is processed as 1. |
| show | boolean | Yes | Whether the preloaded **ListItem** or **ListItemGroup** needs to be displayed. The value **true** means to display the preloaded **ListItem** or **ListItemGroup**, and **false** means not to display the preloaded **ListItem** or **ListItemGroup**.<br> Default value: **false** |

<a id="cachedcount-2"></a>

## cachedCount

```TypeScript
cachedCount(count: number | CacheCountInfo, show: boolean)
```

Sets the number of rows to be preloaded for the list and specifies whether to display the preloaded nodes. In the lazy loading scenario, preloading is performed outside the display area of **List** based on **count** or **CacheCountInfo**. In the non-lazy loading scenario, all child components are loaded.

If the first parameter of the **cachedCount** attribute is of the **number** type, **count** rows are preloaded and laid out both above and below the display area during idle frames.

If the first parameter of the **cachedCount** attribute is of the **CacheCountInfo** type, preloading and layout occur during idle frames when the number of cached rows is less than **CacheCountInfo.minCount**. When the number of cached rows is greater than **CacheCountInfo.maxCount**, the nodes beyond the range are destroyed or recycled for reuse. When the UI is idle (no animation or user operation), **CacheCountInfo.maxCount** rows are preloaded both above and below the display area.

When calculating the number of preloaded rows, the number of **ListItem** rows inside a **ListItemGroup** is counted. If a **ListItemGroup** contains no **ListItem**, the entire **ListItemGroup** is counted as one row. The preloaded nodes can be displayed together with the [clip](arkts-arkui-common-comp-commonmethod-c.md#clip) or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attribute.

Default behavior: The **count** parameter is of the **number** type by default, with its value set based on the number of nodes displayed on the screen, up to a maximum of 16. Preloaded **ListItem** components are not involved in drawing by default.

> **NOTE:** 
> 
> You are advised to set cachedCount to n/2 (n indicates the number of list items displayed on one screen). You
> also need to consider other factors to balance the experience and memory usage. Starting from API version 22,
> setting both minimum and maximum cache counts is supported. The maximum cache count can be set to a moderately
> higher value, such as twice the minimum cache count, to utilize the UI thread's idle time for node creation. This
> reduces the need to create nodes during scrolling for preloading and enhances scrolling smoothness. For best
> practices, see
> [Cache List Items](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list#section11667144010222).

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-ListAttribute-cachedCount(count: number | CacheCountInfo, show: boolean): ListAttribute--><!--Device-ListAttribute-cachedCount(count: number | CacheCountInfo, show: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number &#124; [CacheCountInfo](../arkts-apis/arkts-arkui-cachecountinfo-i.md) | Yes | When the parameter type is number, this parameter indicates the number of preloaded rows in the list.<br>Value range: [0, +∞). If a value less than 0 is set, 1 is used. <br>When the parameter type is **CacheCountInfo**, this parameter indicates the maximum and minimum preloading range. |
| show | boolean | Yes | Whether the preloaded ** or **ListItemGroup** needs to be displayed.<br>**true**: The preloaded **ListItem** or **ListItemGroup** is displayed. <br>**false**: The preloaded **ListItem** or **ListItemGroup** is not displayed. |

## chainAnimation

```TypeScript
chainAnimation(value: boolean)
```

Sets whether to enable the chain linkage effect for the current **List** component.

> **NOTE:** 
> 
> - The chain linkage effect refers to the interaction where, during finger swiping, the dragged **ListItem** acts as the driving object, while adjacent items are driven objects. The driving object drives the linkage of the driven objects, following a physics-based spring animation.
> 
> - The driving effect of the chain linkage effect is reflected in the spacing between **ListItem**s. The spacing in the static state can be set by using the **space** parameter of the **List** component. If the **space**parameter is not set and the chain linkage effect is enabled, the spacing is 20 vp by default.
> 
> - After the chain linkage effect is enabled, the divider of the **List** component is not displayed.
> 
> - The chain linkage effect takes effect only when the **List** component is in single-column mode and the edge effect is of the **EdgeEffect.Spring** type.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-chainAnimation(value: boolean): ListAttribute--><!--Device-ListAttribute-chainAnimation(value: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable chained animations.<br>**false** (default): Chained animations are disabled. **true**: Chained animations are enabled. |

## childrenMainSize

```TypeScript
childrenMainSize(value: ChildrenMainSize)
```

Sets the size information of the child components of a **List** component along the main axis.

> **NOTE:** 
> 
> - This attribute provides the **List** component with the size information of all child components along the main axis, ensuring that the **List** component can maintain the accuracy of its scrolling position in scenarios such as inconsistent main axis sizes of child components, adding or deleting child components, and using [scrollToIndex](arkts-arkui-scroll-comp-scroller-c.md#scrolltoindex). In this way, [scrollTo](arkts-arkui-scroll-comp-scroller-c.md#scrollto) can accurately jump to the specified position, [currentOffset](arkts-arkui-scroll-comp-scroller-c.md#currentoffset) can obtain the current accurate scrolling position, and the built-in scrollbar can move smoothly without jumps.
> 
> - When a child component is a **ListItemGroup**, the overall size of the **ListItemGroup** along the main axis must be accurately calculated based on the number of columns of the **ListItemGroup**, the spacing between
> **ListItem** components along the main axis in the **ListItemGroup**, and the sizes of the header, footer, and
> **ListItem** components in the **ListItemGroup**, and then passed to the **List** component.
> 
> - If there are **ListItemGroup** child components, the [childrenMainSize](arkts-arkui-listitemgroup-comp-attribute.md#childrenmainsize) attribute must be set for each
> **ListItemGroup**. Both the **List** component and each **ListItemGroup** component must bind a
> **ChildrenMainSize** object one-to-one through the **childrenMainSize** attribute interface.
> 
> - In the multi-column scenario, when **LazyForEach** is used to generate child components, ensure that
> **LazyForEach** generates either all **ListItemGroup** components or all **ListItem** components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListAttribute-childrenMainSize(value: ChildrenMainSize): ListAttribute--><!--Device-ListAttribute-childrenMainSize(value: ChildrenMainSize): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ChildrenMainSize](arkts-arkui-common-comp-childrenmainsize-c.md) | Yes | Size information of child components in the main axis direction. |

## contentEndOffset

```TypeScript
contentEndOffset(value: number)
```

Sets the offset from the end of the list content to the boundary of the list display area.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListAttribute-contentEndOffset(value: number): ListAttribute--><!--Device-ListAttribute-contentEndOffset(value: number): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Offset of the end of the content area.<br>Default value: **0**<br>Unit: vp<br>**NOTE:** <br>If this parameter is set to a negative value, the default value is used.<br>Value range: [0, +∞) |

<a id="contentendoffset-1"></a>

## contentEndOffset

```TypeScript
contentEndOffset(offset: number | Resource)
```

Sets the offset from the end of the list content to the boundary of the list display area. Compared with [contentEndOffset&lt;sup&gt;11+&lt;/sup&gt;](#contentendoffset), the parameter name is changed to **offset** and the Resource type is supported.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ListAttribute-contentEndOffset(offset: number | Resource): ListAttribute--><!--Device-ListAttribute-contentEndOffset(offset: number | Resource): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset from the end of the content area.<br>Default value: **0**<br>When the parameter type is number, the unit is vp. <br>If an invalid value such as a negative number or a non- numeric Resource is set, the default value is used.<br>When the parameter type is number, the value range is [0, +∞) |

## contentStartOffset

```TypeScript
contentStartOffset(value: number)
```

Sets the offset from the start of the list content to the boundary of the list display area.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListAttribute-contentStartOffset(value: number): ListAttribute--><!--Device-ListAttribute-contentStartOffset(value: number): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Start offset of the content area.<br>Default value: **0**<br>Unit: vp<br>**Note:** &lt;br/ &gt;If this parameter is set to a negative value, the default value is used.<br>Value range: [0, +∞) |

<a id="contentstartoffset-1"></a>

## contentStartOffset

```TypeScript
contentStartOffset(offset: number | Resource)
```

Sets the offset from the start of the list content to the boundary of the list display area. Compared with [contentStartOffset&lt;sup&gt;11+&lt;/sup&gt;](#contentstartoffset), the parameter name is changed to **offset** and the Resource type is supported.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ListAttribute-contentStartOffset(offset: number | Resource): ListAttribute--><!--Device-ListAttribute-contentStartOffset(offset: number | Resource): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Start offset of the content area.<br>Default value: **0**<br>The unit is vp when the parameter type is number. <br>If an invalid value such as a negative number or a non-numeric Resource is set, the default value is used.<br>Value range when the parameter type is number: [0, +∞) |

## divider

```TypeScript
divider(
    value: ListDividerOptions | null,
  )
```

Sets the style of the divider for the list items. By default, there is no divider.

The divider of **List** is drawn between two child components along the main axis, and no divider is drawn above the first child component or below the last child component. The width of the divider affects the spacing between child components. When the value of **space** or **spaceWidth** is smaller than the divider width, the spacing between child components along the main axis takes the divider width.

In multi-column mode, the value of **startMargin** is calculated from the start edge of the cross axis of each column. In single-column mode, it is calculated from the start edge of the cross axis of the list.

When a list item has [polymorphic styles](arkts-arkui-common-comp.md) applied, the dividers above and below the pressed child component are not rendered.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-divider(    value: ListDividerOptions | null,  ): ListAttribute--><!--Device-ListAttribute-divider(    value: ListDividerOptions | null,  ): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListDividerOptions](arkts-arkui-list-comp-listdivideroptions-i.md) &#124; null | Yes | Style of the divider for the list items.<br>Default value: **null**<br>**Since:** 18 |

## edgeEffect

```TypeScript
edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions)
```

Sets the effect used when the scroll boundary is reached.

> **NOTE:** 
> 
> When the content area of the **List** component is smaller than one screen, there is no rebound effect by
> default. To enable the rebound effect, set the **options** parameter of the **edgeEffect** attribute to
> **{ alwaysEnabled: true }**.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions): ListAttribute--><!--Device-ListAttribute-edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.Spring** |
| options | [EdgeEffectOptions](arkts-arkui-common-comp-edgeeffectoptions-i.md) | No | Whether to enable the sliding effect when the component content is smaller than the component itself. The value **{ alwaysEnabled: true }** enables the sliding effect, and **{ alwaysEnabled: false }** disables it.<br>Default value: **{ alwaysEnabled: false }**<br><br>**Since:** 11 |

## editModeOptions

```TypeScript
editModeOptions(options?: EditModeOptions)
```

Configures the behavior options of the edit mode of the **List** component, including the multi-select aggregation animation switch, preview badge acquisition, and default multi-select style.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ListAttribute-editModeOptions(options?: EditModeOptions): ListAttribute--><!--Device-ListAttribute-editModeOptions(options?: EditModeOptions): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditModeOptions](arkts-arkui-common-comp-editmodeoptions-i.md) | No | Edit mode options, used to customize the feature behavior of the **List** edit mode. This parameter is passed when custom edit mode behavior is required; otherwise, the default configuration is used. |

## enableEditMode

```TypeScript
enableEditMode(enabled: boolean | undefined)
```

Sets whether to enable the edit mode for the **List** component. After the edit mode is enabled, you can swipe to select multiple [ListItem](arkts-arkui-listitem-comp.md) components in the **List** component. If this API is not called, the edit mode is not enabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ListAttribute-enableEditMode(enabled: boolean | undefined): ListAttribute--><!--Device-ListAttribute-enableEditMode(enabled: boolean | undefined): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Whether to enable edit mode. This parameter supports [!!](../../../ui/state-management/arkts-new-binding.md) two-way binding variables.<br>When set to **true**, edit mode is enabled and multiple items can be selected by swiping; when set to **false** or **undefined**, edit mode is disabled and multiple items cannot be selected by swiping. |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

Sets whether to support the scroll gesture.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-enableScrollInteraction(value: boolean): ListAttribute--><!--Device-ListAttribute-enableScrollInteraction(value: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support the scroll gesture. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the [Scroller](arkts-arkui-scroll-comp-scroller-c.md). <br>Default value: **true** |

## focusWrapMode

```TypeScript
focusWrapMode(mode: Optional<FocusWrapMode>)
```

Sets the focus wrap mode for arrow keys.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ListAttribute-focusWrapMode(mode: Optional<FocusWrapMode>): ListAttribute--><!--Device-ListAttribute-focusWrapMode(mode: Optional<FocusWrapMode>): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-common-comp-optional-t.md)&lt;[FocusWrapMode](../arkts-apis/arkts-arkui-focuswrapmode-e.md)&gt; | Yes | Focus wrap mode for cross-axis arrow keys.<br>Default value: **FocusWrapMode.DEFAULT** <br>**NOTE:** <br>Abnormal values are treated as the default value, meaning that cross-axis arrow keys cannot wrap. |

## friction

```TypeScript
friction(value: number | Resource)
```

Sets the friction coefficient. It applies only to gestures in the scrolling area, and it affects only the inertial scrolling process. A value less than or equal to 0 evaluates to the default value.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-friction(value: number | Resource): ListAttribute--><!--Device-ListAttribute-friction(value: number | Resource): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.6** for non-wearable devices and **0.9** for wearable devices.<br>Since API version 11, the default value is **0.7** for non-wearable devices.<br>Since API version 12, the default value is **0.75** for non-wearable devices.<br>Value range: (0, +∞) |

## lanes

```TypeScript
lanes(value: number | LengthConstrain, gutter?: Dimension)
```

Sets the number of columns or rows in the **List** component. (When the **List** is scrolled vertically, the number of columns is displayed. When the **List** is scrolled horizontally, the number of rows is displayed.)

The following example describes how to set the number of columns:

- If **value** is a number, the number of columns is specified based on the number.  
- If **value** is of the **LengthConstrain** type, **minLength** in **LengthConstrain** indicates the minimum  
column width. The **List** component calculates the maximum number of columns based on its minimum column width. In addition, **LengthConstrain** is passed to the child components of the **List** component as the maximum and minimum layout width constraints. These constraints take effect when the child components do not have a specified width.  
- Each list item group occupies one row in multi-column mode. Its child list items are arranged based on the  
**lanes** attribute of the list.  
- If **value** is of the **LengthConstrain** type, the number of columns in **ListItemGroup** is calculated based  
on the width of **ListItemGroup**. Therefore, when the width of **ListItemGroup** is different from that of the **List** component, the number of columns in **ListItemGroup** may be different from that in the **List** component.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-lanes(value: number | LengthConstrain, gutter?: Dimension): ListAttribute--><!--Device-ListAttribute-lanes(value: number | LengthConstrain, gutter?: Dimension): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; LengthConstrain | Yes | Number of columns or rows in the layout of the **List** component.<br> Default value: **1**<br>Value range: [1, +∞). If a value less than 1 is passed, the default value is used. |
| gutter | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | No | Column spacing or row spacing.<br>Default value: **0**<br>When the parameter type is number, the unit is vp.<br>Value range: [0, +∞).If a negative value is passed, the default value is used. <br>**NOTE:** <br>**gutter** specifies the column spacing or row spacing, which takes effect only when the number of columns or rows is greater than 1.<br> |

<a id="lanes-1"></a>

## lanes

```TypeScript
lanes(value: number | LengthConstrain | ItemFillPolicy, gutter?: Dimension)
```

Sets the number of layouts and the spacing along the cross axis of the **List** component. When **List** scrolls vertically, this attribute sets the number of columns and the column spacing. When **List** scrolls horizontally, this attribute sets the number of rows and the row spacing. By default, the list is displayed in one column or one row. In multi-column or multi-row mode, a **ListItemGroup** occupies one row exclusively when scrolling vertically and one column exclusively when scrolling horizontally. The **ListItem** components in a **ListItemGroup** are laid out according to the value set by the **lanes** attribute of the **List** component.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

<!--Device-ListAttribute-lanes(value: number | LengthConstrain | ItemFillPolicy, gutter?: Dimension): ListAttribute--><!--Device-ListAttribute-lanes(value: number | LengthConstrain | ItemFillPolicy, gutter?: Dimension): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; LengthConstrain &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of layouts in the cross axis direction of the current **List** component. When the **List** scrolls vertically, it indicates the number of columns; when it scrolls horizontally, it indicates the number of rows.<br>When set to the number type, the number of columns or rows is determined by the numeric value. The value range of the number type is [1, +∞). If a value less than 1 is passed, the default value is used.<br> When set to the LengthConstrain type, the number of columns is determined by the maximum and minimum column widths when the **List** scrolls vertically, and the number of rows is determined by the maximum and minimum row heights when it scrolls horizontally.<br> When set to the ItemFillPolicy type, the number of columns is determined by the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the **List** component width. This type takes effect only when the **List** scroll direction is vertical. |
| gutter | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | No | When the **List** scrolls vertically, it indicates the column spacing; when it scrolls horizontally, it indicates the row spacing.<br><br>When the parameter type is number, the unit is vp.<br> If a negative value is passed, the default value is used.<br>**NOTE:** <br>This takes effect only when the number of columns or rows is greater than 1. <br>The value must be greater than or equal to 0. Default value: **0**. |

## listDirection

```TypeScript
listDirection(value: Axis)
```

Sets the direction in which the list items are arranged.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-listDirection(value: Axis): ListAttribute--><!--Device-ListAttribute-listDirection(value: Axis): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [Axis](../arkts-apis/arkts-arkui-axis-e.md) | Yes | Direction in which the list items are arranged.<br>Default value: **Axis.Vertical** |

## maintainVisibleContentPosition

```TypeScript
maintainVisibleContentPosition(enabled: boolean)
```

Sets whether to maintain the visible content's position when data is inserted or deleted outside the display area of the component.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListAttribute-maintainVisibleContentPosition(enabled: boolean): ListAttribute--><!--Device-ListAttribute-maintainVisibleContentPosition(enabled: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to maintain the visible content's position when data is inserted or deleted outside the visible area of the component.<br>Default value: **false** <br>**false**: The visible content position will change when data is inserted or deleted. **true**: The visible content position remains unchanged when data is inserted or deleted. |

## multiSelectable

```TypeScript
multiSelectable(value: boolean)
```

Sets whether to enable multiselect.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-multiSelectable(value: boolean): ListAttribute--><!--Device-ListAttribute-multiSelectable(value: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable multiselect.<br>**false** (default): Multiselect is disabled. **true**: Multiselect is enabled. |

## nestedScroll

```TypeScript
nestedScroll(value: NestedScrollOptions)
```

Sets the nested scrolling mode in the forward and backward directions to implement scrolling linkage with the parent component.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-nestedScroll(value: NestedScrollOptions): ListAttribute--><!--Device-ListAttribute-nestedScroll(value: NestedScrollOptions): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-common-comp-nestedscrolloptions-i.md) | Yes | Nested scrolling options.<br>Default value: **{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }** |

## onEditModeChange

```TypeScript
onEditModeChange(callback: Callback<boolean> | undefined)
```

Triggered when the edit mode state changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

<!--Device-ListAttribute-onEditModeChange(callback: Callback<boolean> | undefined): ListAttribute--><!--Device-ListAttribute-onEditModeChange(callback: Callback<boolean> | undefined): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; &#124; undefined | Yes | Callback invoked when the edit mode state changes.<br>The value **true** indicates entering the edit mode, and **false** indicates exiting the edit mode. <br>If **undefined** is passed in, the callback is canceled. |

## onItemDragEnter

```TypeScript
onItemDragEnter(event: (event: ItemDragInfo) => void)
```

Triggered when a dragged child component [ListItem](arkts-arkui-listitem-comp.md) of **List** enters the list range.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-onItemDragEnter(event: (event: ItemDragInfo) => void): ListAttribute--><!--Device-ListAttribute-onItemDragEnter(event: (event: ItemDragInfo) => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo) =&gt; void | Yes | Information about the drag point. |

## onItemDragLeave

```TypeScript
onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void)
```

Triggered when a dragged child component [ListItem](arkts-arkui-listitem-comp.md) of **List** leaves the list range.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void): ListAttribute--><!--Device-ListAttribute-onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number) =&gt; void | Yes | Information about the drag point. |

## onItemDragMove

```TypeScript
onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void)
```

Triggered when a dragged child component [ListItem](arkts-arkui-listitem-comp.md) of **List** moves within the list range.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void): ListAttribute--><!--Device-ListAttribute-onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number) =&gt; void | Yes | Information about the drag point. |

## onItemDragStart

```TypeScript
onItemDragStart(event: OnItemDragStartCallback)
```

Triggered when dragging of a child component [ListItem](arkts-arkui-listitem-comp.md) of **List** starts.

Automatic scrolling of **List** is not supported when dragging to the edge of **List**. You can use the [onMove](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-drag-sorting.md#onmove) API of **ForEach**, **LazyForEach**, and **Repeat** to implement this effect. For details, see [Example 12: Implementing Dragging with OnMove](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#example-12-implementing-dragging-with-onmove). Note that the [onMove](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-drag-sorting.md#onmove) API does not support dragging across **ListItemGroup** components.

> **NOTE:** 
> 
> This API can be called within [attributeModifier](arkts-arkui-common-comp-commonmethod-c.md#attributemodifier) since API version 14.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-onItemDragStart(event: OnItemDragStartCallback): ListAttribute--><!--Device-ListAttribute-onItemDragStart(event: OnItemDragStartCallback): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnItemDragStartCallback](arkts-arkui-common-comp-onitemdragstartcallback-t.md) | Yes | Callback invoked when the [ListItem](arkts-arkui-listitem-comp.md) child component of the **List** starts to be dragged. <br> In API version 22 and earlier versions, the type of this parameter is **(event: ItemDragInfo, itemIndex: number) =&gt; (() =&gt; any) &#124; void**, where the meanings of the **event** and **itemIndex** parameters are described in [OnItemDragStartCallback](arkts-arkui-common-comp-onitemdragstartcallback-t.md).<br>**Since:** 23 |

## onItemDrop

```TypeScript
onItemDrop(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void)
```

Triggered when the dragged item is dropped on the drop target of the list.

During dragging across lists, **isSuccess** is set to **true** if the drop target is bound to **onItemDrop**. Otherwise, **isSuccess** is set to **false**. During dragging within a list, **isSuccess** is the return value of the **onItemMove** event.

**Since:** 8

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-onItemDrop(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void): ListAttribute--><!--Device-ListAttribute-onItemDrop(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) =&gt; void | Yes | Information about the drag point. |

## onItemMove

```TypeScript
onItemMove(event: (from: number, to: number) => boolean)
```

Triggered when a child component [ListItem](arkts-arkui-listitem-comp.md) of **List** moves.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-onItemMove(event: (from: number, to: number) => boolean): ListAttribute--><!--Device-ListAttribute-onItemMove(event: (from: number, to: number) => boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (from: number, to: number) =&gt; boolean | Yes |  |

## onReachEnd

```TypeScript
onReachEnd(event: () => void)
```

Called when the list reaches the end position. This callback is triggered when the last child component appears in the list view due to scrolling or content/layout changes.

If the child component does not fill the list and can be completely displayed in the list without scrolling, this event is triggered during the first loading.

When the list edge scrolling effect is the spring effect, this event is triggered once when the list passes the end position and is triggered again when the list returns to the end position.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onReachEnd(event: () => void): ListAttribute--><!--Device-ListAttribute-onReachEnd(event: () => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the list reaches the end position. |

## onReachStart

```TypeScript
onReachStart(event: () => void)
```

Triggered when the list reaches the start position.

This event is triggered once when **initialIndex** is **0** during list initialization and once when the list scrolls to the start position. When the list edge scrolling effect is the spring effect, this event is triggered once when the list passes the start position and is triggered again when the list returns to the start position.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onReachStart(event: () => void): ListAttribute--><!--Device-ListAttribute-onReachStart(event: () => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the list reaches the start position. |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

When this API is called back, the event parameter passes the scroll offset that is about to occur. The event processing function can calculate the actually required scroll offset based on the application scenario and return it as the return value. The list will then scroll according to this returned actual scroll offset.

If **listDirection** is set to **Axis.Vertical**, the return value is the amount by which the list needs to scroll in the vertical direction. If **listDirection** is set to **Axis.Horizontal**, the return value is the amount by which the list needs to scroll in the horizontal direction.

This event is triggered when either of the following conditions is met:

1. Scrolling is initiated by user interaction (for example, finger swipe, keyboard, or mouse operation).
2. The **List** component scrolls by inertia.
3. Call the [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) API to trigger scrolling.

This event is not triggered in the following scenarios:

1. A scroll control API other than [fling](arkts-arkui-scroll-comp-scroller-c.md#fling) is called.
2. The out-of-bounds bounce effect is active.
3. The scrollbar is dragged.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): ListAttribute--><!--Device-ListAttribute-onScrollFrameBegin(event: OnScrollFrameBeginCallback): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-scroll-comp-onscrollframebegincallback-t.md) | Yes | Callback triggered when each frame scrolling starts.<br>**Since:** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (start: number, end: number, center: number) => void)
```

Triggered when a child component enters or leaves the list display area. During index calculation, each **ListItemGroup** component is taken as a whole and assigned an index, and the indexes of the list items within are not included in the calculation.

> **NOTE:** 
> 
> Compared with [onScrollVisibleContentChange](#onscrollvisiblecontentchange), **onScrollIndex**
> counts a **ListItemGroup** as one index value as a whole, and the callback returns only the first, last, and
> middle index values. To obtain the detailed index information of the header, footer, or **ListItem** inside a
> **ListItemGroup**, use **onScrollVisibleContentChange**.
> When the list edge scrolling effect is the spring effect, the **onScrollIndex** event is not triggered when the
> user scrolls the list to the edge or releases the list to rebound.

This event is triggered once when the list is initialized and when the index of the first child component or the last child component in the list display area changes.

Since API version 10, this event is also triggered when the child component in the center of the list display area changes.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onScrollIndex(event: (start: number, end: number, center: number) => void): ListAttribute--><!--Device-ListAttribute-onScrollIndex(event: (start: number, end: number, center: number) => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (start: number, end: number, center: number) =&gt; void | Yes |  |

## onScrollStart

```TypeScript
onScrollStart(event: () => void)
```

Triggered when the list starts scrolling initiated by the user's finger dragging the list or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) starts.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onScrollStart(event: () => void): ListAttribute--><!--Device-ListAttribute-onScrollStart(event: () => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the list starts scrolling. |

## onScrollStop

```TypeScript
onScrollStop(event: () => void)
```

Triggered when the list stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroll-comp-scroller-c.md) stops.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onScrollStop(event: () => void): ListAttribute--><!--Device-ListAttribute-onScrollStop(event: () => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the list stops sliding. |

## onScrollVisibleContentChange

```TypeScript
onScrollVisibleContentChange(handler: OnScrollVisibleContentChangeCallback)
```

Triggered when a child component enters or leaves the list display area. During index calculation, the list item, header of the list item group, and footer of the list item group each are counted as a child component.

When the list edge scrolling effect is the spring effect, the **onScrollVisibleContentChange** event is not triggered when the user scrolls the list to the edge or releases the list to rebound.

This event is triggered once when the list is initialized and when the index of the first child component or the last child component in the list display area changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

<!--Device-ListAttribute-onScrollVisibleContentChange(handler: OnScrollVisibleContentChangeCallback): ListAttribute--><!--Device-ListAttribute-onScrollVisibleContentChange(handler: OnScrollVisibleContentChangeCallback): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnScrollVisibleContentChangeCallback](arkts-arkui-list-comp-onscrollvisiblecontentchangecallback-t.md) | Yes | Callback invoked when the displayed content changes. |

## scrollBar

```TypeScript
scrollBar(value: BarState)
```

Sets the scrollbar state.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-scrollBar(value: BarState): ListAttribute--><!--Device-ListAttribute-scrollBar(value: BarState): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [BarState](../arkts-apis/arkts-arkui-barstate-e.md) | Yes | Scrollbar state.<br>In API version 9 and earlier versions, the default value is **BarState.Off**. Since API version 10, the default value is **BarState.Auto**. |

## scrollSnapAlign

```TypeScript
scrollSnapAlign(value: ScrollSnapAlign)
```

Sets the scroll snap alignment effect for list items when scrolling ends.

This API is available only when the heights of list items are the same. During the alignment animation, the scroll operation source type reported by the [onWillScroll](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#onwillscroll12) event is **ScrollSource.FLING**.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

<!--Device-ListAttribute-scrollSnapAlign(value: ScrollSnapAlign): ListAttribute--><!--Device-ListAttribute-scrollSnapAlign(value: ScrollSnapAlign): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScrollSnapAlign](arkts-arkui-list-comp-scrollsnapalign-e.md) | Yes | Alignment mode of the scroll snap position.<br>Default value: **ScrollSnapAlign.NONE** |

## scrollSnapAnimationSpeed

```TypeScript
scrollSnapAnimationSpeed(speed: ScrollSnapAnimationSpeed)
```

Sets the speed of the snap animation for list item scrolling. This parameter takes effect only when the scroll alignment effect is set.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

<!--Device-ListAttribute-scrollSnapAnimationSpeed(speed: ScrollSnapAnimationSpeed): ListAttribute--><!--Device-ListAttribute-scrollSnapAnimationSpeed(speed: ScrollSnapAnimationSpeed): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | [ScrollSnapAnimationSpeed](arkts-arkui-list-comp-scrollsnapanimationspeed-e.md) | Yes | Speed of the snap animation for listing scrolling.<br>Default value: **ScrollSnapAnimationSpeed.NORMAL** |

## stackFromEnd

```TypeScript
stackFromEnd(enabled: boolean)
```

Whether the list's layout starts from the bottom (end) rather than the top (beginning).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

<!--Device-ListAttribute-stackFromEnd(enabled: boolean): ListAttribute--><!--Device-ListAttribute-stackFromEnd(enabled: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the list's layout starts from the bottom (end) rather than the top (beginning).<br>**false** (default): The layout starts from the top. **true**: The layout starts from the bottom. |

## sticky

```TypeScript
sticky(value: StickyStyle)
```

Used together with the [ListItemGroup](arkts-arkui-listitemgroup-comp.md) component to set whether the header of a **ListItemGroup** is sticky at the top or the footer is sticky at the bottom. Since API version 20, the **sticky** attribute supports the **StickyStyle.BOTH** enum value, which can be directly set to **StickyStyle.BOTH** to support both sticky header and sticky footer, with the same effect as **StickyStyle.Header | StickyStyle.Footer**. Before API version 20, the same effect can be achieved through **StickyStyle.Header | StickyStyle.Footer**.

> **NOTE:** 
> 
> Occasionally, after **sticky** is set, floating-point calculation precision may result in small gaps appearing
> during scrolling. To address this issue, you can apply the [pixelRound](arkts-arkui-common-comp-commonmethod-c.md#pixelround) attribute
> to the current component, which rounds down the pixel values and helps eliminate the gaps.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-sticky(value: StickyStyle): ListAttribute--><!--Device-ListAttribute-sticky(value: StickyStyle): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [StickyStyle](arkts-arkui-list-comp-stickystyle-e.md) | Yes | Whether to pin the header to the top or the footer to the bottom in the list item group.<br>Default value: **StickyStyle.None** |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

Defines whether the **List** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. If this attribute is not set, empty branch nodes are not supported. This attribute cannot be updated after being set. Therefore, you cannot switch between the behavior of supporting empty branches and the behavior of not supporting empty branches after setting this attribute.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

<!--Device-ListAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): ListAttribute--><!--Device-ListAttribute-supportEmptyBranchInLazyLoading(supported: boolean | undefined): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean &#124; undefined | Yes | Whether the current **List** component supports using the [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) rendering control syntax in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) to generate an empty branch node that contains no child components.<br>The value **true** indicates that the empty branch node is supported, and **false** indicates that it is not supported.<br>If the value is undefined, it is processed as **false**. |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

Sets whether to synchronously load all child components in the list.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-ListAttribute-syncLoad(enable: boolean): ListAttribute--><!--Device-ListAttribute-syncLoad(enable: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to synchronously load all child components in the list.<br>**true**: yes; **false**: no Default value: **true** <br>**NOTE:** <br>When this parameter is set to **false**, in the first display or **scrollToIndex** jumps without animation, if the time consumed by the frame layout exceeds 50 ms, the child components that have not been laid out in the list are delayed to the next frame for layout. |

## editMode

```TypeScript
editMode(value: boolean)
```

Sets whether the current **List** component is in editable mode.

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. This API has been completely
> removed, and no substitute is provided. To switch the edit state and delete list items, you can control the
> display and hiding of the delete button through a custom state variable and update the data source in the click
> event of the delete button. For details, see
> [Example 3: Customizing Edit and Delete Mode](arkts-arkui-list-comp.md).

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ListAttribute-editMode(value: boolean): ListAttribute--><!--Device-ListAttribute-editMode(value: boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether the current **List** component is in editable mode. The value **true** indicates that the current **List** component is in editable mode, and **false** indicates that it is not.<br>Default value: **false** |

## onItemDelete

```TypeScript
onItemDelete(event: (index: number) => boolean)
```

Triggered when a list item is deleted.

**Since:** 7

**Deprecated since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-ListAttribute-onItemDelete(event: (index: number) => boolean): ListAttribute--><!--Device-ListAttribute-onItemDelete(event: (index: number) => boolean): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (index: number) =&gt; boolean | Yes |  |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)
```

Triggered when the list scrolls.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** onDidScroll

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-ListAttribute-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): ListAttribute--><!--Device-ListAttribute-onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void): ListAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) =&gt; void | Yes | Callback when scroll, scrollOffset: Offset relative to the previous frame. The offset is positive when the list content scrolls up and negative when the list content scrolls down.<br>Unit: vp scrollState: Current scroll state. |
