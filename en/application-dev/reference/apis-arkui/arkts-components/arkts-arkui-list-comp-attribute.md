# List properties/events

In addition to universal attributes and [scrollable component common attributes](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#attributes), the following attributes are also supported.

In addition to universal events and [scrollable component common events](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#events), the following events are also supported.

**Inheritance/Implementation:** ListAttribute extends ScrollableCommonMethod<ListAttribute>

**Since:** 7

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## alignListItem

```TypeScript
alignListItem(value: ListItemAlign)
```

Sets the layout mode of list items along the cross axis when the cross-axis width of the list is greater than the value calculated by the following formula: cross-axis width of list items × lanes + (lanes – 1) × gutter.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListItemAlign](arkts-arkui-listitemalign-e.md) | Yes | Alignment mode of list items along the cross axis.<br>Default value: **ListItemAlign.Start** |

## backPressBehavior

```TypeScript
backPressBehavior(behavior: ListBackPressBehavior | undefined)
```

Sets the system back button behavior of the **List** component.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| behavior | [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md) &#124; undefined | Yes | System back button behavior of the **List** component. Currently, you can use the [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md) parameter to configure whether to collapse the expanded swipe-out component of a **ListItem** when the system back button takes effect.<br>If this parameter is set to **undefined**, the default behavior is restored. That is, when the system back button takes effect, the expanded swipe-out component of the **ListItem** is collapsed. |

## cachedCount

```TypeScript
cachedCount(value: number)
```

Sets the number of **ListItem** or **ListItemGroup** components to be preloaded (cached). In a lazy loading scenario, only the **cachedCount** rows of **ListItem** components above and below the visible area of the **List** component is preloaded. In a non-lazy loading scenario, all items are loaded at once. For both lazy and non-lazy loading, only the content within the list display area plus the content equivalent to **cachedCount** outside the display area is laid out. <!--Del-->For details, see [Minimizing White Blocks During Swiping](../../../performance/arkts-performance-improvement-recommendation.md#minimizing-white-blocks-during-swiping).<!--DelEnd-->

When **cachedCount** is set for the list, the system preloads and lays out the **cachedCount**-specified number of rows of list items both above and below the currently visible area of the list. When calculating the number of rows for list items, the system takes into account the number of rows from the list items within a list item group. If a list item group does not contain any list items, then the entire list item group is counted as one row.

When a list is nested with **LazyForEach**, and within **LazyForEach** there is a list item group, **LazyForEach** will create **cachedCount**-specified number of list item groups both above and below the currently visible area of the list.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Number of list items or list item groups to be preloaded (cached).<br>Default value: number of nodes visible on the screen, with the maximum value of 16<br>Value range: 0, +∞).<br>Values less than 0 are treated as **1**. |

## cachedCount

```TypeScript
cachedCount(count: number, show: boolean)
```

Sets the number of list items or list item groups to be cached (preloaded) and specifies whether to display the preloaded nodes.

When **cachedCount** is set for the list, the system preloads and lays out the **cachedCount**-specified number of rows of list items both above and below the currently visible area of the list. When calculating the number of rows for list items, the system takes into account the number of rows from the list items within a list item group. If a list item group does not contain any list items, then the entire list item group is counted as one row. This attribute can be combined with the [clip or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attributes to display the preloaded nodes.

> **NOTE:** 
> 
> You are advised to set cachedCount to n/2 (n indicates the number of list items displayed on one screen). You
> also need to consider other factors to balance the experience and memory usage. For best practices, see
> [Cache List Items](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list#section11667144010222).

**Since:** 14

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 14.

**Widget capability:** This API can be used in ArkTS widgets since API version 14.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number | Yes | Number of list items to be preloaded.<br>Default value: number of nodes visible on the screen, with the maximum value of 16<br>Value range: 0, +∞).<br>Values less than 0 are treated as **1**. |
| show | boolean | Yes | Whether to display the preloaded list items. If this parameter is set to **true**, the preloaded list items are displayed. If this parameter is set to **false**, the preloaded list items are not displayed.<br> Default value: **false** |

## cachedCount

```TypeScript
cachedCount(count: number | CacheCountInfo, show: boolean)
```

Sets the number of list items or list item groups to be cached (preloaded) and specifies whether to display the preloaded nodes.

If the first parameter of the **cachedCount** attribute is of the **number** type, a specified number (specified by **count**) of rows of list items will be preloaded and laid out above and below the visible area during idle frames.

If the first parameter of the **cachedCount** attribute is of the **CacheCountInfo** type, preloading and layout will occur during idle frames when the number of cached rows is less than **CacheCountInfo.minCount**. When the number of cached rows is greater than **CacheCountInfo.maxCount**, the nodes outside the specified range will be destroyed or reused. When the UI is idle (no animation or user operation), a specified number (specified by **CacheCountInfo.maxCount**) of rows of list items will be preloaded above and below the visible area.

When calculating the number of rows for list items, the system takes into account the number of rows from the list items within a list item group. If a list item group does not contain any list items, then the entire list item group is counted as one row. This attribute can be combined with the [clip or [clipContent](../../../reference/apis-arkui/arkui-ts/ts-container-scrollable-common.md#clipcontent14) attributes to display the preloaded nodes.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| count | number &#124; [CacheCountInfo](../arkts-apis/arkts-arkui-cachecountinfo-i.md) | Yes | Number of preloaded **ListItem** components if the parameter is of the **number** type.<br>Value range: [0, +∞).<br>Values less than 0 are treated as **1**. <br>If the parameter type is CacheCountInfo, the parameter indicates the maximum and minimum preloading range. |
| show | boolean | Yes | Whether to display the preloaded list items.<br>**true**: yes<br>**false**: no |

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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
> - This attribute provides the **List** component with the size of all child components in the main-axis direction. This ensures that the **List** component can maintain the accuracy of the scrolling position in scenarios such as varying main-axis sizes among child components, adding or removing child components, or using [scrollToIndex](arkts-arkui-scroller-c.md#scrolltoindex). In this way, scrollTo can accurately jump to the specified position, currentOffset can obtain the accurate scroll position, and the built-in scroll bar can be smoothly moved without jumps.
> 
> - If a child component is **ListItemGroup**, the overall size of **ListItemGroup** in the main-axis direction needs to be accurately calculated based on the column count of **ListItemGroup**, the spacing between list items in **ListItemGroup** in the main-axis direction, and the size of the header, footer, and **ListItem** components in **ListItemGroup**. This calculated size must then be passed to the **List** component.
> 
> - If a child component contains **ListItemGroup** components, the childrenMainSize attribute must be set for each
> **ListItemGroup** component. The **List** component and each **ListItemGroup** component must be bound to a
> **ChildrenMainSize** object through the **childrenMainSize** attribute in one-to-one mode.
> 
> - For a multi-column list where child components are generated using **LazyForEach**, ensure that **LazyForEach**generates either all **ListItemGroup** components or all **ListItem** components.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ChildrenMainSize](arkts-arkui-childrenmainsize-c.md) | Yes | Size information of child components in the main axis direction. |

## contentEndOffset

```TypeScript
contentEndOffset(value: number)
```

Sets the offset from the end of the list content to the boundary of the list display area.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Offset from the end of the list content to the boundary of the list display area.<br> Default value: **0**<br>Unit: vp<br>**NOTE:** <br>If the set value is a negative number, the default value will be used. |

## contentEndOffset

```TypeScript
contentEndOffset(offset: number | Resource)
```

Sets the offset from the end of the list content to the boundary of the list display area. Compared with [contentEndOffset&lt;sup&gt;11+&lt;/sup&gt;](#contentendoffset), the parameter name is changed to **offset** and the Resource type is supported.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset from the end of the list content to the boundary of the list display area.<br>Default value: **0**<br>If the parameter type is number, the unit is vp.<br>Invalid values (negative numbers or non-numeric Resource values) are treated as the default value. |

## contentStartOffset

```TypeScript
contentStartOffset(value: number)
```

Sets the offset from the start of the list content to the boundary of the list display area.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 11

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Offset from the start of the list content to the boundary of the list display area.<br> Default value: **0**<br>Unit: vp<br>**NOTE:** <br>If the set value is a negative number, the default value will be used. |

## contentStartOffset

```TypeScript
contentStartOffset(offset: number | Resource)
```

Sets the offset from the start of the list content to the boundary of the list display area. Compared with [contentStartOffset&lt;sup&gt;11+&lt;/sup&gt;](#contentstartoffset), the parameter name is changed to **offset** and the Resource type is supported.

If the sum of **contentStartOffset** and **contentEndOffset** exceeds the length of the list content area, both offsets are reset to **0**.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Offset from the start of the list content to the boundary of the list display area.<br>Default value: **0**<br>If the parameter type is number, the unit is vp.<br>Invalid values (negative numbers or non-numeric Resource values) are treated as the default value. |

## divider

```TypeScript
divider(
    value: ListDividerOptions | null,
  )
```

Sets the style of the divider for the list items. By default, there is no divider.

The divider is drawn between list items along the main axis, and not above the first list item and below the last list item.

In multi-column mode, the value of **startMargin** is calculated from the start edge of the cross axis of each column. In single-column mode, it is calculated from the start edge of the cross axis of the list.

When a list item has polymorphic styles applied, the dividers above and below the pressed child component are not rendered.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) &#124; null | Yes | Style of the divider for the list items.<br>Default value: **null**<br>**Since:** 18 |

## edgeEffect

```TypeScript
edgeEffect(value: EdgeEffect, options?: EdgeEffectOptions)
```

Sets the effect used when the scroll boundary is reached.

> **NOTE:** 
> 
> By default, this component can produce a bounce effect only when there is more than one screen of content. To
> produce a bounce effect when there is less than one screen of content, set the **options** parameter of the
> **edgeEffect** attribute to **{ alwaysEnabled: true }**.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [EdgeEffect](../arkts-apis/arkts-arkui-edgeeffect-e.md) | Yes | Effect used when the scroll boundary is reached. The spring and shadow effects are supported.<br>Default value: **EdgeEffect.Spring** |
| options | [EdgeEffectOptions](arkts-arkui-edgeeffectoptions-i.md) | No | Whether to enable the scroll effect when the component content is smaller than the component itself. The value **{ alwaysEnabled: true }** means to enable the scroll effect, and **{ alwaysEnabled: false }** means the opposite.<br>Default value: **{ alwaysEnabled: false }**<br>**Since:** 11 |

## editMode

```TypeScript
editMode(value: boolean)
```

Sets whether to enable edit mode. For details about how to delete selected list items, see [Example 3](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#example-3-setting-the-edit-mode).

> **NOTE:** 
> 
> This API is supported since API version 7 and deprecated since API version 9. No substitute is provided.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to enable edit mode.<br>Default value: **false** (the edit mode is disabled). |

## editModeOptions

```TypeScript
editModeOptions(options?: EditModeOptions)
```

Configures the options of the edit mode.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [EditModeOptions](arkts-arkui-editmodeoptions-i.md) | No | Edit mode options. |

## enableEditMode

```TypeScript
enableEditMode(enabled: boolean | undefined)
```

Sets whether to enable the edit mode for the **List** component. After the edit mode is enabled, you can swipe to select multiple ListItem components in the **List** component. If this API is not called, the edit mode is not enabled.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean &#124; undefined | Yes | Whether to enable the edit mode.<br>**true** means to enable the edit mode and swiping to select multiple items is supported; **false** or **undefined** means to disable the edit mode and swiping to select multiple items is not supported. |

## enableScrollInteraction

```TypeScript
enableScrollInteraction(value: boolean)
```

Sets whether to support the scroll gesture.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | boolean | Yes | Whether to support the scroll gesture. With the value **true**, scrolling via finger or mouse is enabled. With the value **false**, scrolling via finger or mouse is disabled, but this does not affect the scrolling APIs of the [Scroller](arkts-arkui-scroller-c.md).<br>Default value: **true** |

## focusWrapMode

```TypeScript
focusWrapMode(mode: Optional<FocusWrapMode>)
```

Sets the focus wrap mode for arrow keys.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [Optional](arkts-arkui-optional-t.md)&lt;[FocusWrapMode](../arkts-apis/arkts-arkui-focuswrapmode-e.md)&gt; | Yes | Focus wrap mode for cross-axis arrow keys.<br>Default value: **FocusWrapMode.DEFAULT**<br>**NOTE:** <br>Abnormal values are treated as the default value, meaning that cross- axis arrow keys cannot wrap. |

## friction

```TypeScript
friction(value: number | Resource)
```

Sets the friction coefficient. It applies only to gestures in the scrolling area, and it affects only the inertial scrolling process. A value less than or equal to 0 evaluates to the default value.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; [Resource](../arkts-apis/arkts-arkui-resource-t.md) | Yes | Friction coefficient.<br>Default value: **0.6** for non-wearable devices and **0.9** for wearable devices.<br>Since API version 11, the default value for non-wearable devices is **0.7**.<br>Since API version 12, the default value for non-wearable devices is **0.75**. |

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; LengthConstrain | Yes | Number of columns or rows in the list.<br>Default value: **1**<br>Value range: [1, +∞) |
| gutter | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | No | Column gap or row gap.<br>Default value: **0** <br>Value range: [0, +∞) <br>**NOTE:** <br>This parameter takes effect when the number of columns or rows is greater than 1.<br>**Since:** 10 |

## lanes

```TypeScript
lanes(value: number | LengthConstrain | ItemFillPolicy, gutter?: Dimension)
```

Sets the number of columns and the column spacing of the **List** component. By default, the **List** component is displayed in one column.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**Widget capability:** This API can be used in ArkTS widgets since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number &#124; LengthConstrain &#124; [ItemFillPolicy](../arkts-apis/arkts-arkui-itemfillpolicy-i.md) | Yes | Number of columns in the layout of the **List** component.<br> If this parameter is set to a number, the number of columns is determined by this value. The value range of the number type is [1, +∞).<br>If this parameter is set to a value of the **LengthConstrain** type, the number of columns is determined based on the maximum and minimum values specified in **LengthConstrain**. <br>If this parameter is set to a value of the **ItemFillPolicy** type, the number of columns is determined based on the [breakpoint type](../../../ui/arkts-layout-development-grid-layout.md#breakpoints) corresponding to the width of the **List** component. This type takes effect only when the scrolling direction of the list is vertical. |
| gutter | [Dimension](../arkts-apis/arkts-arkui-dimension-t.md) | No | Gap between columns.<br>Default value: **0**<br>Value range: [0, +∞) |

## listDirection

```TypeScript
listDirection(value: Axis)
```

Sets the direction in which the list items are arranged.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to maintain the visible content's position when data is inserted or deleted outside the visible area of the component.<br>Default value: **false**<br>**false**: The visible content position will change when data is inserted or deleted. **true**: The visible content position remains unchanged when data is inserted or deleted. |

## multiSelectable

```TypeScript
multiSelectable(value: boolean)
```

Sets whether to enable multiselect.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [NestedScrollOptions](arkts-arkui-nestedscrolloptions-i.md) | Yes | Nested scrolling options.<br>Default value: **{ scrollForward: NestedScrollMode.SELF_ONLY, scrollBackward: NestedScrollMode.SELF_ONLY }** |

## onEditModeChange

```TypeScript
onEditModeChange(callback: Callback<boolean> | undefined)
```

Triggered when the editing mode status changes.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | Callback&lt;boolean&gt; &#124; undefined | Yes | Callback triggered when editing mode status changes.<br>Passing undefined will unregister the callback. |

## onItemDelete

```TypeScript
onItemDelete(event: (index: number) => boolean)
```

Triggered when a list item is deleted.

**Since:** 7

**Deprecated since:** 9

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (index: number) =&gt; boolean | Yes |  |

## onItemDragEnter

```TypeScript
onItemDragEnter(event: (event: ItemDragInfo) => void)
```

Called when a dragged list item enters the list.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo) =&gt; void | Yes | Information about the drag point. |

## onItemDragLeave

```TypeScript
onItemDragLeave(event: (event: ItemDragInfo, itemIndex: number) => void)
```

Triggered when the dragged item leaves the drop target of the list.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number) =&gt; void | Yes |  |

## onItemDragMove

```TypeScript
onItemDragMove(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number) => void)
```

Triggered when the dragged item moves over the drop target of the list.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number) =&gt; void | Yes |  |

## onItemDragStart

```TypeScript
onItemDragStart(event: OnItemDragStartCallback)
```

Triggered when a list item starts to be dragged.

Automatic scrolling of the list cannot be triggered when a list item is dragged to the edge of the list. You can use the [onMove](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-drag-sorting.md#onmove) API of **ForEach**, **LazyForEach**, or **Repeat** to implement this effect. For details, see [Example 12: Implementing Dragging with OnMove](../../../reference/apis-arkui/arkui-ts/ts-container-list.md#example-12-implementing-dragging-with-onmove). However, note that the [onMove](../../../reference/apis-arkui/arkui-ts/ts-universal-attributes-drag-sorting.md#onmove) API does not support cross-**ListItemGroup** dragging.

> **NOTE:** 
> 
> This API can be called within attributeModifier since API version 14.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md) | Yes | Callback triggered when the dragging of a list item starts.<br> In API version 22 and earlier versions, the parameter type is **(event: ItemDragInfo, itemIndex: number) =&gt; (() =&gt; any) &#124; void**. For details about the **event** and **itemIndex** parameters, see [OnItemDragStartCallback](arkts-arkui-onitemdragstartcallback-t.md).<br>**Since:** 23 |

## onItemDrop

```TypeScript
onItemDrop(event: (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) => void)
```

Triggered when the dragged item is dropped on the drop target of the list. During dragging across lists, **isSuccess** is set to **true** if the drop target is bound to **onItemDrop**. Otherwise, **isSuccess** is set to **false**. During dragging within a list, **isSuccess** is the return value of the **onItemMove** event.

**Since:** 8

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (event: ItemDragInfo, itemIndex: number, insertIndex: number, isSuccess: boolean) =&gt; void | Yes | Callback triggered when dragging is stopped within the scope of the list.<br>event: Information about the drag point. <br>itemIndex: Initial position of the dragged item. <br>insertIndex: Index of the position to which the dragged item is dropped. <br> isSuccess: Whether the dragged item is successfully dropped. If the return value is **true**, the list item is successfully dropped. If the return value is **false**, the list item is not successfully dropped. |

## onItemMove

```TypeScript
onItemMove(event: (from: number, to: number) => boolean)
```

Triggered when a list item moves.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback triggered when the list reaches the start position. |

## onScroll

```TypeScript
onScroll(event: (scrollOffset: number, scrollState: ScrollState) => void)
```

Triggered when the list scrolls.

**Since:** 7

**Deprecated since:** 12

**Substitutes:** onDidScroll

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (scrollOffset: number, scrollState: ScrollState) =&gt; void | Yes | Callback when scroll, scrollOffset: Offset relative to the previous frame. The offset is positive when the list content scrolls up and negative when the list content scrolls down.<br>Unit: vp scrollState: Current scroll state. |

## onScrollFrameBegin

```TypeScript
onScrollFrameBegin(event: OnScrollFrameBeginCallback)
```

When this API is called back, the event parameter passes the scroll offset that is about to occur. The event processing function can calculate the actually required scroll offset based on the application scenario and return it as the return value. The list will then scroll according to this returned actual scroll offset.

If **listDirection** is set to **Axis.Vertical**, the return value is the amount by which the list needs to scroll in the vertical direction. If **listDirection** is set to **Axis.Horizontal**, the return value is the amount by which the list needs to scroll in the horizontal direction.

This event is triggered when either of the following conditions is met:

1. Scrolling is initiated by user interaction (for example, finger swipe, keyboard, or mouse operation).
2. The **List** component scrolls by inertia.
3. Call the fling API to trigger scrolling.

This event is not triggered in the following scenarios:

1. A scroll control API other than fling is called.
2. The out-of-bounds bounce effect is active.
3. The scrollbar is dragged.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | [OnScrollFrameBeginCallback](arkts-arkui-onscrollframebegincallback-t.md) | Yes | Callback triggered when each frame scrolling starts.<br>**Since:** 20 |

## onScrollIndex

```TypeScript
onScrollIndex(event: (start: number, end: number, center: number) => void)
```

Triggered when a child component enters or leaves the list display area.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | (start: number, end: number, center: number) =&gt; void | Yes |  |

## onScrollStart

```TypeScript
onScrollStart(event: () => void)
```

Triggered when the list starts scrolling initiated by the user's finger dragging the list or its scrollbar. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroller-c.md) starts.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | () =&gt; void | Yes | Callback invoked when the list starts scrolling. |

## onScrollStop

```TypeScript
onScrollStop(event: () => void)
```

Triggered when the list stops scrolling after the user's finger leaves the screen. This event is also triggered when the animation contained in the scrolling triggered by [Scroller](arkts-arkui-scroller-c.md) stops.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

This event is triggered once when the list is initialized and when the index of the first child component or the next child component in the list display area changes.

**Since:** 12

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 12.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| handler | [OnScrollVisibleContentChangeCallback](arkts-arkui-onscrollvisiblecontentchangecallback-t.md) | Yes | Callback invoked when the displayed content changes. |

## scrollBar

```TypeScript
scrollBar(value: BarState)
```

Sets the scrollbar state.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ScrollSnapAlign](arkts-arkui-scrollsnapalign-e.md) | Yes | Alignment mode of the scroll snap position.<br>Default value: **ScrollSnapAlign.NONE** |

## scrollSnapAnimationSpeed

```TypeScript
scrollSnapAnimationSpeed(speed: ScrollSnapAnimationSpeed)
```

Sets the speed of the snap animation for list item scrolling. This parameter takes effect only when the scroll alignment effect is set.

**Since:** 22

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 22.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| speed | [ScrollSnapAnimationSpeed](arkts-arkui-scrollsnapanimationspeed-e.md) | Yes | Speed of the snap animation for listing scrolling.<br>Default value: **ScrollSnapAnimationSpeed.NORMAL** |

## stackFromEnd

```TypeScript
stackFromEnd(enabled: boolean)
```

Whether the list's layout starts from the bottom (end) rather than the top (beginning).

**Since:** 19

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 19.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether the list's layout starts from the bottom (end) rather than the top (beginning).<br>**false** (default): The layout starts from the top. **true**: The layout starts from the bottom. |

## sticky

```TypeScript
sticky(value: StickyStyle)
```

Sets whether to pin the header to the top or the footer to the bottom in the list item group, if set. To support both the pin-to-top and pin-to-bottom features, set **sticky** to **StickyStyle.Header \| StickyStyle.Footer**. From API version 20, the **sticky** attribute can also be set to **StickyStyle.BOTH** to enable both sticky header and sticky footer at the same time.

> **NOTE:** 
> 
> Occasionally, after **sticky** is set, floating-point calculation precision may result in small gaps appearing
> during scrolling. To address this issue, you can apply the [pixelRound](arkts-arkui-commonmethod-c.md#pixelround) attribute
> to the current component, which rounds down the pixel values and help eliminate the gaps.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [StickyStyle](arkts-arkui-stickystyle-e.md) | Yes | Whether to pin the header to the top or the footer to the bottom in the list item group.<br>Default value: **StickyStyle.None** |

## supportEmptyBranchInLazyLoading

```TypeScript
supportEmptyBranchInLazyLoading(supported: boolean | undefined)
```

Defines whether the **List** component supports the generation of empty branch nodes that do not contain any child components using the **if/else** rendering control syntax in **LazyForEach** or **Repeat**. If this attribute is not set, empty branch nodes are not supported. This attribute cannot be updated after being set. Therefore, you cannot switch between the behavior of supporting empty branches and the behavior of not supporting empty branches after setting this attribute.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 23.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| supported | boolean &#124; undefined | Yes | Whether the current **List** component supports the use of the [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) rendering syntax in [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md) or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md) to generate an empty branch node that contains no child component.<br>**true**: yes; **false**: no<br>If the value is **undefined**, it is processed as **false**. |

## syncLoad

```TypeScript
syncLoad(enable: boolean)
```

Sets whether to synchronously load all child components in the list.

**Since:** 20

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enable | boolean | Yes | Whether to synchronously load all child components in the list.<br>**true**: yes; **false**: no Default value: **true**<br>**NOTE:** <br>When this parameter is set to **false**, in the first display or **scrollToIndex** jumps without animation, if the time consumed by the frame layout exceeds 50 ms, the child components that have not been laid out in the list are delayed to the next frame for layout. |
