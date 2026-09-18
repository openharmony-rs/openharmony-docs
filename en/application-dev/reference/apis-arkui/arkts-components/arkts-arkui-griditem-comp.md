# GridItem

The **GridItem** component provides a single item in a grid.

> **NOTE** > > * > > * This component can be used only as a child of Grid. > > * When this component is used with > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), its child components are > created when it is created. When this component is used with > [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) or > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), or when the parent component is > **Grid**, its child components are created when it is laid out. > > * If a **Grid** component contains a large number of **GridItem** components, using > [columnStart](arkts-arkui-griditem-comp-attribute.md#columnstart)/[columnEnd](arkts-arkui-griditem-comp-attribute.md#columnend) or > [rowStart](arkts-arkui-griditem-comp-attribute.md#rowstart)/[rowEnd](arkts-arkui-griditem-comp-attribute.md#rowend) to set the size of > **GridItem** components can lead to performance issues, especially when **scrollToIndex** is used to scroll to a > specific index. This is because **Grid** will traverse all **GridItem** nodes sequentially to find the specified > index, which can be time-consuming. To address this issue, it is recommended that you use > [GridLayoutOptions](arkts-arkui-gridlayoutoptions-i.md) for layout, which significantly improves the efficiency of finding the > position of **GridItem** components. For best practices, see > [Optimizing Frame Loss for Grid Component Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve_grid_performance).

## Child Components

This component can contain a single child component.

## GridItem

```TypeScript
GridItem(value?: GridItemOptions)
```

Creates a **GridItem** component.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GridItemOptions](arkts-arkui-griditemoptions-i.md) | No | Parameters of the grid item, containing the **style** parameter of the [GridItemStyle](arkts-arkui-griditemstyle-e.md) enum type. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [GridItemOptions](arkts-arkui-griditemoptions-i.md) | Defines the style of a grid item. |

### Enums

| Name | Description |
| --- | --- |
| [GridItemStyle](arkts-arkui-griditemstyle-e.md) | Enumerates styles of grid items. |

## Examples

```TypeScript
### Example 1: Setting the Grid Item Position

The GridItem component sets its own position by setting reasonable rowStart, rowEnd, columnStart, and columnEnd attributes. For scenarios where you need to specify the start row and column and the occupied rows and columns of GridItem, it is recommended to use the [GridLayoutOptions](ts-container-grid.md#gridlayoutoptions10) parameter of Grid. For details, refer to [Example 1: Creating a Fixed Row and Column Grid Layout](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns) of Grid.


```

```TypeScript
### Example 2: Setting the Grid Item Style

This example shows how to set the grid item style using GridItemOptions.
```
