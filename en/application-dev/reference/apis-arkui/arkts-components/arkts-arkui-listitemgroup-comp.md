# ListItemGroup

The **ListItemGroup** component is used to display list item groups. It must be used with the List component. Unless specified otherwise, it spans the entire width of the **List** component.

Lazy loading of **ListItemGroup** loads the child components in the visible area as required. Compared with full loading, lazy loading can improve the application startup speed and reduce the memory usage. The lazy loading capabilities vary when the **ListItemGroup** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When **ListItemGroup** is used together with **ForEach**, all child nodes are created at a time. The nodes within
the screen range are laid out and rendered when needed. When a user swipes, the nodes that are out of the screen range are not removed from the tree, and the nodes that are within the screen range are laid out and rendered.
- When **ListItemGroup** is used together with **LazyForEach**, all nodes within the screen range are created, laid
out, and rendered at a time. When a user swipes, the nodes that are out of the screen range are removed from the tree, and the nodes that are within the screen range are created, laid out, and rendered.
- When the **ListItemGroup** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the lazy loading behavior is the same as that of **LazyForEach**. When the **ListItemGroup** component is used together with **Repeat** without **virtualScroll**, the lazy loading behavior is the same as that of **ForEach**.

Preloading in **ListItemGroup** refers to loading not only the visible child components within the display area but also some invisible child components outside the display area during idle time. Preloading can reduce frame loss during scrolling and improve smoothness. Preloading takes effect only when lazy loading is used. The preloading capabilities vary when the **ListItemGroup** component is used together with [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), or [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md).

- When the **ListItemGroup** component is used together with **ForEach** and
cachedCount is set, in addition to laying out child components within the display area, child components within the range of **cachedCount** outside the display area are pre-laid out during idle time based on the **cachedCount** attribute of the **List** component.
- When the **ListItemGroup** component is used together with **LazyForEach** and
cachedCount is set, in addition to creating and laying out child components within the display area, child components within the range of **cachedCount** outside the display area are created and pre-laid out during idle time based on the **cachedCount** attribute of the **List** component.
- When the **ListItemGroup** component is used together with **Repeat** with
[virtualScroll](arkts-arkui-repeat-comp-attribute.md#virtualscroll), the preloading behavior is the same as that of **LazyForEach**. When the **ListItemGroup** component is used together with **Repeat** without **virtualScroll**, the preloading behavior is the same as that of **ForEach**.

> **NOTE**

> - This component can be used only as a child of List. > > - The **ListItemGroup** component does not support the universal attribute > [aspectRatio](arkts-arkui-commonmethod-c.md#aspectratio). > > - If the parent **List** component of **ListItemGroup** has its [listDirection](arkts-arkui-list-comp-attribute.md#listdirection) > attribute set to **Axis.Vertical**, setting the > universal attribute height has no effect. In this case, the height of > the **ListItemGroup** component is fixed at the sum of the component's header height, footer height, and total > height of the list items. > > - If the parent **List** component of **ListItemGroup** has its **listDirection** attribute set to > **Axis.Horizontal**, setting the universal attribute width has no > effect. In this case, the width of the **ListItemGroup** component is fixed at the sum of the component's header > width, footer width, and total width of the list items. > > - The list items in the **ListItemGroup** component cannot be edited or dragged. This means that their > editable attribute does not take effect. > > - The **ListItemGroup** ignores the **direction** attribute for setting the layout direction; instead, it adopts > the layout direction of its parent **List** component.

## Child Components

Contains the ListItem child component. Child components can be dynamically generated using rendering control types [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md), [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), and [Repeat](../../../ui/rendering-control/arkts-new-rendering-control-repeat.md). **LazyForEach** or **Repeat** is recommended to optimize performance.

## ListItemGroup

```TypeScript
ListItemGroup(options?: ListItemGroupOptions)
```

Creates a **ListItemGroup** component.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [ListItemGroupOptions](arkts-arkui-listitemgroupoptions-i.md) | No | Parameters of the list item group. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [ListItemGroupOptions](arkts-arkui-listitemgroupoptions-i.md) | Describes the **ListItemGroup** component parameter. |

### Enums

| Name | Description |
| --- | --- |
| [ListItemGroupHeaderFooterStyle](arkts-arkui-listitemgroupheaderfooterstyle-e.md) | Enumerates the header and footer styles of **ListItemGroup**. |
| [ListItemGroupStyle](arkts-arkui-listitemgroupstyle-e.md) | Enumerates the card styles of the **ListItemGroup** component. |

## Examples

```TypeScript
### Example 1: Setting a Sticky Header and Footer

This example uses [sticky](ts-container-list.md#sticky9) to implement the sticky header and footer.

ListDataSource implements the LazyForEach data source API [IDataSource](ts-rendering-control-lazyforeach.md#idatasource), which is used to provide child components for List and ListItemGroup through LazyForEach.
```

```TypeScript

```

```TypeScript
### Example 2: Applying a Card-style Effect

This example illustrates the card-style effect of the ListItemGroup component.


```

```TypeScript
### Example 3: Setting Header and Footer

This example uses ComponentContent to set the header and footer.

For details about ListDataSource and the complete code, see [Example 1: Setting a Sticky Header and Footer](#example-1-setting-a-sticky-header-and-footer).


```

```TypeScript
### Example 4: Setting a Multi-Column Layout

This example shows how ListItemGroup is used in a multi-column layout. The multi-column layout is implemented by setting the [lanes](ts-container-list.md#lanes9) attribute of the List component.

For details about ListDataSource and the complete code, see [Example 1: Setting a Sticky Header and Footer](#example-1-setting-a-sticky-header-and-footer).


```

```TypeScript
### Example 5: Setting Floating State

This example sets the [headerStyle](arkts-arkui-listitemgroupoptions-i.md) of ListItemGroup to [ListItemGroupHeaderFooterStyle.FLOATING](arkts-arkui-listitemgroupheaderfooterstyle-e.md) to implement the floating display effect of the group header during scrolling.
```
