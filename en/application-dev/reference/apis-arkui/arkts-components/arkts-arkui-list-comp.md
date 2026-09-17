# List

The **List** component provides a list container that presents a series of list items arranged in a column with the same width. It supports presentations of the same type of data in a multiple and coherent row style, for example, images or text.

Lazy loading of **List** loads the child components in the visible area as required. Compared with full loading, lazy loading can improve the app startup speed and reduce the memory usage. The lazy loading capabilities vary when the **List** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When **List** is used together with **ForEach**, all child nodes are created at a time. The nodes within the screen
range are laid out and rendered when needed. When a user swipes, the nodes that are out of the screen range are not removed from the tree, and the nodes that are within the screen range are laid out and rendered.
- When **List** is used together with **LazyForEach**, all nodes within the screen range are created, laid out, and
rendered at a time. When a user swipes, the nodes that are out of the screen range are removed from the tree, and the nodes that are within the screen range are created, laid out, and rendered.
- When the **List** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the lazy loading behavior is the same as that of **LazyForEach**. When the **List** component is used together with **Repeat** without **virtualScroll**, the lazy loading behavior is the same as that of **ForEach**.

If a scrollable component is nested in a **List** component, their scrolling directions are the same, and the main axis size is not set for the **List** component, the **List** component loads all child components. As a result, lazy loading does not take effect. In this scenario, you are advised to use the ListItemGroup component to optimize the performance.

Preloading in **List** refers to loading not only the visible child components within the display area but also some invisible child components outside the display area during idle time. Preloading can reduce frame loss during scrolling and improve smoothness. Preloading takes effect only when lazy loading is used. You can set the number of components to be preloaded for the **List** component using [cachedCount](arkts-arkui-list-comp-attribute.md#cachedcount). By default, child components equivalent to one screen above and below the visible area are preloaded (up to a maximum of 16 rows). The preloading capabilities vary when the **List** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When the **List** component is used together with **ForEach** and **cachedCount** is set, in addition to laying out
child components within the visible area, child components within the range of **cachedCount** outside the visible area are pre-laid out during idle time.
- When the **List** component is used together with **LazyForEach** and **cachedCount** is set, in addition to
creating and laying out child components within the display area, child components within the range of **cachedCount** outside the display area are pre-created and pre-laid out during idle time.
- When the **List** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the preloading behavior is the same as that of **LazyForEach**. When the **List** component is used together with **Repeat** without **virtualScroll**, the preloading behavior is the same as that of **ForEach**.

> **NOTE**

> The component has been bound with gestures to implement functions such as follow-up scrolling. If you need to add > custom gestures, refer to Gesture Blocking Enhancement.

## Child Components

Only the ListItem and ListItemGroup child components and custom components are supported. When using custom components inside **List**, you are advised to wrap the custom component with a **ListItem** or **ListItemGroup** as the top-level container. Setting attributes or event methods directly on custom components is not recommended.

Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

> **NOTE:** 
> 
> If performance lag occurs when you process a large number of child components, consider using lazy loading, list
> item caching, dynamic preloading, component reuse, and layout optimization. For best practices, see
> [Optimizing Frame Loss for Long List Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-best-practices-long-list).
> 
> Starting from API version 21, the maximum width or height for a single child component inside a **List** container
> is 16,777,216 px. In API version 20 and earlier versions, the limit was 1,000,000 px. If a child component exceeds
> the applicable size limit, scrolling or display behavior may become abnormal.
> 
> Below are the rules for calculating the indexes of the child components of **List**:
> 
> - The index increases in ascending order of child components.
> 
> - In the **if/else** statement, only the child components for which the condition evaluates to true participate in the index calculation.
> 
> - In the **ForEach**, **LazyForEach**, or **Repeat** statement, the indexes of all expanded subnodes are calculated.
> 
> - After changes occur in [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md),[ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md),[LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md), index values are updated accordingly for child components.
> 
> - Each **ListItemGroup** component is taken as a whole and assigned an index, and the indexes of the list items within are not included in the index calculation.
> 
> - Child components of **List** whose **visibility** attribute is set to **Hidden** or **None** are included in the index calculation.

## List

```TypeScript
List(options?: ListOptions)
```

Creates a list container.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ListOptions](arkts-arkui-listoptions-i.md) | No | Options of the **List** component. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ChainAnimationOptions](arkts-arkui-chainanimationoptions-i-sys.md) | Defines the chain animation options. |
| [CloseSwipeActionOptions](arkts-arkui-closeswipeactionoptions-i.md) | Implements the callbacks and events for the ListItem in the [expanded](arkts-arkui-swipeactionstate-e.md) state. |
| [ListBackPressBehavior](arkts-arkui-listbackpressbehavior-i.md) | Defines the system back button behavior of the **List** component. |
| [ListDividerOptions](arkts-arkui-listdivideroptions-i.md) | Defines the divider style of the list or list item group. |
| [ListOptions](arkts-arkui-listoptions-i.md) | Defines the options of the **List** component. |
| [UIListEvent](arkts-arkui-uilistevent-i.md) | Represents the return value of the [getEvent('List')](../arkts-apis/arkts-arkui-typenode-getevent-f.md) method in **frameNode**, which can be used to set scroll events for a **List** node. |
| [VisibleListContentInfo](arkts-arkui-visiblelistcontentinfo-i.md) | Describes the details of the child components in the visible area of a list. |

### Types

| Name | Description |
| --- | --- |
| [OnListScrollIndexCallback](arkts-arkui-onlistscrollindexcallback-t.md) | Represents a callback for item changes in the visible area of the **List** component. |
| [OnScrollVisibleContentChangeCallback](arkts-arkui-onscrollvisiblecontentchangecallback-t.md) | Triggered when a child component enters or leaves the list display area. |

### Enums

| Name | Description |
| --- | --- |
| [ChainEdgeEffect](arkts-arkui-chainedgeeffect-e-sys.md) | Declare edge effect of chain animation. |
| [ListItemAlign](arkts-arkui-listitemalign-e.md) | Sets the alignment mode of child components in the cross-axis direction of the list. |
| [ListItemGroupArea](arkts-arkui-listitemgrouparea-e.md) | Enumerates the areas of **ListItemGroup**. |
| [ScrollSnapAlign](arkts-arkui-scrollsnapalign-e.md) | Enumerates the alignment modes of list items when scrolling ends. |
| [ScrollSnapAnimationSpeed](arkts-arkui-scrollsnapanimationspeed-e.md) | Enumerates the speeds of the snap animation for list scrolling. |
| [ScrollState](arkts-arkui-scrollstate-e.md) | Enumerates the scrolling states. |
| [StickyStyle](arkts-arkui-stickystyle-e.md) | Enumerates the sticky styles. |

## Examples

```TypeScript
### Example 1: Adding a Scroll Event

In this example, a vertical list is implemented, and a callback is invoked when the first or last item displayed in the list changes.

ListDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for List through LazyForEach.
```

```TypeScript

```

```TypeScript
### Example 2: Setting Child Element Alignment

This example showcases the alignment effects of child elements in the cross-axis direction of the List component using different ListItemAlign enumeration values.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 3: Customizing Edit and Delete Mode

This example shows how to control the display and hiding of the delete button through a custom state variable and update the data source in the click event of the delete button to implement the list item deletion effect.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 4: Setting the Alignment Mode for the Scroll Snap Position

This example shows how to configure the List component to align the scroll snap position to the center.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 5: Implementing Accurate Scrolling

This example shows that, by setting the [childrenMainSize](#childrenmainsize12) attribute, the list can jump to an exact specific location when the scrollTo API is called, even when the heights of the child components are inconsistent.

For usage with state management V2, see [List and makeObserved](../../../ui/state-management/arkts-v1-v2-migration-inner-object.md#scrollable-component).

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 6: Obtaining Child Component Index Information

This example demonstrates how to obtain index information of list items in a List component when groups are involved.


```

```TypeScript
### Example 7: Setting Edge Fading

This example demonstrates how to implement a List component with an edge fading effect and set the length of the fading edge.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 8: Setting the Single-Side Edge Effect

This example demonstrates how to set a single-side edge effect for the List component using the edgeEffect API.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 9: Setting Focus Wrap on a List

In API version 20 and later versions, this example uses the [focusWrapMode](#focuswrapmode20) API to implement the effect of line-wrapping focus navigation with arrow keys in the List component.


```

```TypeScript
### Example 10: Keeping the Display Content Unchanged When Data Is Inserted Outside the Display Area

This example uses the maintainVisibleContentPosition API to implement infinite loading of historical messages when the screen is swiped up.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 11: Setting the Margin of the Scrollbar

Starting from API version 20, this example shows how to use the [scrollBarMargin](./ts-container-scrollable-common.md#scrollbarmargin20) attribute to set the scrollbar margin and avoid the [contentStartOffset](#contentstartoffset11) and [contentEndOffset](#contentendoffset11) areas.


```

```TypeScript
### Example 12: Implementing Dragging with OnMove

Starting from API version 12, this example demonstrates how to use the [onMove](./ts-universal-attributes-drag-sorting.md#onmove) API of ForEach to sort items by dragging them. The list can automatically scroll when an item is dragged to the edge of the list.


```

```TypeScript
### Example 13: Configuring Lanes Based on Breakpoints

In API version 22 and later versions, this example shows how to configure lanes in the List component based on breakpoints.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).

When the list width is within the breakpoint range of sm or smaller, two columns are displayed.



When the list width is within the breakpoint range of md, three columns are displayed.



When the list width is within the breakpoint range of lg or larger, five columns are displayed.


```

```TypeScript
### Example 14: Obtaining the Total Content Size

This example demonstrates how to obtain the total content size of the List component. This functionality is supported since API version 22.


```

```TypeScript
### Example 15: Dragging Between Two Lists

This example implements the dragging effect of ListItem between two List components through events such as onItemDragStart.


```

```TypeScript
### Example 16: Centering the Clicked Item in ListItemGroup

This example uses the [scrollToItemInGroup](arkts-arkui-listscroller-c.md#scrolltoitemingroup) API to implement the effect of centering the [ListItem](./ts-container-listitem.md) component in the [ListItemGroup](./ts-container-listitemgroup.md) when the ListItem is clicked.


```

```TypeScript
### Example 17: Setting the Multi-Selection Gather Animation

This example demonstrates how to gather selected list items in the visible area when a long press is performed on list items using [bindContextMenu](ts-universal-attributes-menu.md#bindcontextmenu8), with the multi-selection gather animation switch enabled for List.

Since API version 23, the [editModeOptions](#editmodeoptions23) API is added to the List component  to set the multi-selection gather animation switch.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).


```

```TypeScript
### Example 18: Implementing Swipe-based Multi-Selection

This example implements the finger-swipe multi-select effect on List by using the [enableEditMode](#enableeditmode) API and the [onEditModeChange](#oneditmodechange) event.

Since API version 26.0.0, the List component adds the enableEditMode API and the onEditModeChange event.

For details about ListDataSource and the complete code, see [Example 1: Adding a Scroll Event](#example-1-adding-a-scroll-event).
```
