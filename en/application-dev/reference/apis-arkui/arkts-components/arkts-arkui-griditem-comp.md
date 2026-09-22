# GridItem

The **GridItem** component provides a single item in a grid.

> **NOTE** > > * > > * This component can be used only as a child of Grid. > > * When this component is used with > [LazyForEach](../../../ui/rendering-control/arkts-rendering-control-lazyforeach.md), its child components are > created when it is created. When this component is used with > [if/else](../../../ui/rendering-control/arkts-rendering-control-ifelse.md) or > [ForEach](../../../ui/rendering-control/arkts-rendering-control-foreach.md), or when the parent component is > **Grid**, its child components are created when it is laid out. > > * If a **Grid** component contains a large number of **GridItem** components, using > [columnStart](arkts-arkui-griditem-comp-attribute.md#columnstart)/[columnEnd](arkts-arkui-griditem-comp-attribute.md#columnend) or > [rowStart](arkts-arkui-griditem-comp-attribute.md#rowstart)/[rowEnd](arkts-arkui-griditem-comp-attribute.md#rowend) to set the size of > **GridItem** components can lead to performance issues, especially when **scrollToIndex** is used to scroll to a > specific index. This is because **Grid** will traverse all **GridItem** nodes sequentially to find the specified > index, which can be time-consuming. To address this issue, it is recommended that you use > [GridLayoutOptions](arkts-arkui-grid-comp-gridlayoutoptions-i.md) for layout, which significantly improves the efficiency of finding the > position of **GridItem** components. For best practices, see > [Optimizing Frame Loss for Grid Component Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve_grid_performance).

## Child Components

This component can contain a single child component.

## GridItem

```TypeScript
GridItem(value?: GridItemOptions)
```

Creates a **GridItem** component.

**Since:** 7

**Model restriction:** This API can be used in both the stage model and FA model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GridItemOptions](arkts-arkui-griditem-comp-griditemoptions-i.md) | No | Parameters of the grid item, containing the **style** parameter of the [GridItemStyle](arkts-arkui-griditem-comp-griditemstyle-e.md) enum type. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [GridItemOptions](arkts-arkui-griditem-comp-griditemoptions-i.md) | Defines the style of a grid item. |

### Enums

| Name | Description |
| --- | --- |
| [GridItemStyle](arkts-arkui-griditem-comp-griditemstyle-e.md) | Enumerates styles of grid items. |

## Examples

### Example 1: Setting the Grid Item Position

The GridItem component sets its own position by setting reasonable rowStart, rowEnd, columnStart, and columnEnd attributes. For scenarios where you need to specify the start row and column and the occupied rows and columns of GridItem, it is recommended to use the [GridLayoutOptions](ts-container-grid.md#gridlayoutoptions10) parameter of Grid. For details, refer to [Example 1: Creating a Fixed Row and Column Grid Layout](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Example 3: Implementing a Scrollable Grid with Grid Items Spanning Rows and Columns](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns) of Grid.



```TypeScript
// xxx.ets
@Entry
@Component
struct GridItemExample {
  @State numbers: string[] = ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', '10', '11', '12', '13', '14', '15'];

  build() {
    Column() {
      Grid() {
        GridItem() {
          Text('4')
            .fontSize(16)
            .backgroundColor(0xFAEEE0)
            .width('100%')
            .height('100%')
            .textAlign(TextAlign.Center)
        }.rowStart(1).rowEnd(2).columnStart(1).columnEnd(2) // Set valid row and column numbers.

        ForEach(this.numbers, (item: string) => {
          GridItem() {
            Text(item)
              .fontSize(16)
              .backgroundColor(0xF9CF93)
              .width('100%')
              .height('100%')
              .textAlign(TextAlign.Center)
          }
        }, (item: string) => item)

        GridItem() {
          Text('5')
            .fontSize(16)
            .backgroundColor(0xDBD0C0)
            .width('100%')
            .height('100%')
            .textAlign(TextAlign.Center)
        }.columnStart(1).columnEnd(4) // No row number is set, so positioning does not follow columnStart(1). Here, the layout starts from row 5, column index 0, and spans 4 columns.
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr 1fr 1fr')
      .width('90%').height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 2: Setting the Grid Item Style

This example shows how to set the grid item style using GridItemOptions.

```TypeScript
// xxx.ets
@Entry
@Component
struct GridItemExample {
  @State numbers: string[] = ['0', '1', '2'];

  build() {
    Column({ space: 5 }) {
      Grid() {
        ForEach(this.numbers, (rowItem: string) => {
          ForEach(this.numbers, (item: string) => {
            GridItem({ style: GridItemStyle.NONE }) {
              Text(item)
                .fontSize(16)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
                .focusable(true)
            }
            .backgroundColor(0xF9CF93)
          }, (item: string) => item)
        }, (rowItem: string) => rowItem)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr')
      .columnsGap(4)
      .rowsGap(4)
      .width('60%')
      .backgroundColor(0xFAEEE0)
      .height(150)
      .padding(4)

      Grid() {
        ForEach(this.numbers, (rowItem: string) => {
          ForEach(this.numbers, (item: string) => {
            GridItem({ style: GridItemStyle.PLAIN }) {
              Text(item)
                .fontSize(16)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
                .focusable(true)
            }
            .backgroundColor(0xF9CF93)
          }, (item: string) => item)
        }, (rowItem: string) => rowItem)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr')
      .columnsGap(4)
      .rowsGap(4)
      .width('60%')
      .backgroundColor(0xFAEEE0)
      .height(150)
      .padding(4)
    }.width('100%').margin({ top: 5 })
  }
}
```
