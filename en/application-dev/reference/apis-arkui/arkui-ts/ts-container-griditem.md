# GridItem

The **GridItem** component provides a single item in a grid.

>  **NOTE**
>
>  * This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>  * This component can be used only as a child of [Grid](ts-container-grid.md).
>  * When this component is used with **LazyForEach**, its child components are created when it is created. When this component is used with **if/else** or **ForEach**, or when the parent component is **Grid**, its child components are created when it is laid out.
>  * If a **Grid** container contains a large number of **GridItem** components, using **columnStart/columnEnd** or **rowStart/rowEnd** to set the size of **GridItem** components can lead to performance issues, especially when **scrollToIndex** is used to scroll to a specific index. This is because the **Grid** will traverse all **GridItem** nodes sequentially to find the specified index, which can be time-consuming. To address this issue, it is recommended that you use **GridLayoutOptions** for layout, which significantly improves the efficiency of finding the position of **GridItem** components. For best practices, see [Optimizing Frame Loss for Grid Component Loading](https://developer.huawei.com/consumer/en/doc/best-practices/bpta-improve_grid_performance).

## Child Components

This component can contain a single child component.

## APIs

GridItem(value?: GridItemOptions)

Creates a **GridItem** component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                     | Mandatory| Description                                                    |
| ------ | --------------------------------------------- | ---- | ------------------------------------------------------------ |
| value<sup>11+</sup>  | [GridItemOptions](#griditemoptions11) | No  | Parameters of the grid item, containing the **style** parameter of the [GridItemStyle](#griditemstyle11) enum type.|

## Attributes

### rowStart

rowStart(value: number)

Sets the start row number of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| value  | number | Yes  | Start row number of the component.<br>In situations where you need to designate the start row and column numbers as well as the number of rows and columns a grid item spans, you are advised to use the [layoutOptions parameter](ts-container-grid.md#gridlayoutoptions10) of the **Grid** component. For reference, see [Grid Example 1](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Grid Example 3](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns).<br>Value range: [0, Total number of rows – 1].|

### rowEnd

rowEnd(value: number)

Sets the end row number of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| value  | number | Yes  | End row number of the component.<br>In situations where you need to designate the start row and column numbers as well as the number of rows and columns a grid item spans, you are advised to use the [layoutOptions parameter](ts-container-grid.md#gridlayoutoptions10) of the **Grid** component. For reference, see [Grid Example 1](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Grid Example 3](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns).<br>Value range: [0, Total number of rows – 1].|

### columnStart

columnStart(value: number)

Sets the start column number of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| value  | number | Yes  | Start column number of the component.<br>In situations where you need to designate the start row and column numbers as well as the number of rows and columns a grid item spans, you are advised to use the [layoutOptions parameter](ts-container-grid.md#gridlayoutoptions10) of the **Grid** component. For reference, see [Grid Example 1](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Grid Example 3](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns).<br>Value range: [0, Total number of columns – 1].|

### columnEnd

columnEnd(value: number)

Sets the end column number of the component.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type  | Mandatory| Description              |
| ------ | ------ | ---- | ------------------ |
| value  | number | Yes  | End column number of the component.<br>In situations where you need to designate the start row and column numbers as well as the number of rows and columns a grid item spans, you are advised to use the [layoutOptions parameter](ts-container-grid.md#gridlayoutoptions10) of the **Grid** component. For reference, see [Grid Example 1](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Grid Example 3](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns).<br>Value range: [0, Total number of columns – 1].|

>  **NOTE**
>
>  In situations where you need to designate the start row and column numbers as well as the number of rows and columns a grid item spans, you are advised to use the [layoutOptions parameter](ts-container-grid.md#gridlayoutoptions10) of the **Grid** component. For reference, see [Grid Example 1](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Grid Example 3](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns).
>
>  Rules for setting **rowStart**, **rowEnd**, **columnStart**, and **columnEnd**:
>
> * The valid value range of **rowStart** and **rowEnd** is 0 to the total number of rows minus 1. The valid value range of **columnStart** and **columnEnd** is 0 to the total number of columns minus 1.
>
> * If **rowStart**, **rowEnd**, **columnStart**, or **columnEnd** is set, the grid item occupies the specified number of rows (**rowEnd** - **rowStart** + 1) or columns (**columnEnd** - **columnStart** + 1).
>
> * Settings outside of the valid ranges do not take effect.
>
> * In the grid that has both **columnTemplate** and **rowTemplate** set, grid items that have **rowStart**/**rowEnd** or **columnStart**/**columnEnd** set are laid out in a row-by-row then column-by-column manner.
>
>  * In the grid that has only **columnTemplate** set, grid items that have **columnStart**/**columnEnd** set are laid out in the specified columns. If there are already grid items in those columns, the grid items will be laid out in another row.
>
> * In the grid that has only **rowTemplate** set, grid items that have **rowStart**/**rowEnd** set are laid out on the specified rows. If there are already grid items in those rows, the grid items will be laid out in another column.
>
> * In the grid that has neither **columnTemplate** nor **rowTemplate** set, the row and column number attributes do not work.
>  
>  The following table describes the rules for handling abnormal values for **GridItem** row and column numbers.
>
>  | Attribute Setting | Exception Type | Correction Applied |
>  | ----- |----| ------------------------ |
>  | Only **columnTemplate** set | Invalid row or column value | Single-row and single-column layout |                 |
>  | Only **rowTemplate** set | Invalid row or column value | Single-row and single-column layout | |
>  | Both **rowTemplate** and **columnTemplate** set |  **rowStart** < **rowEnd** | Row span = min(rowEnd-rowStart+1, total number of rows) |
>  | Both **rowTemplate** and **columnTemplate** set | **rowStart** > **rowEnd** | Single-row and single-column layout |
>  | Both **rowTemplate** and **columnTemplate** set | **columnStart** < **columnEnd** | Column span = min(columnEnd-columnStart+1, total number of rows), total number of columns) |
>  | Both **rowTemplate** and **columnTemplate** set | **columnStart** > **columnEnd** | Single-row and single-column layout |

### forceRebuild<sup>(deprecated)</sup>

forceRebuild(value: boolean)

Whether to re-create the component when it is being built. Whether to re-create the component is automatically determined based on the component attributes and child component changes. No manual configuration is required.

This API is deprecated since API version 9.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                   |
| ------ | ------- | ---- | ------------------------------------------------------- |
| value  | boolean | Yes  | Sets whether to re-create the component when it is being built.<br>Default value: **false**|

### selectable<sup>8+</sup>

selectable(value: boolean)

Sets whether the grid item is selectable in the mouse selection box area. This attribute takes effect only when mouse box selection is enabled for the parent **Grid** container.

This attribute must be used before the [style for the selected state](./ts-universal-attributes-polymorphic-style.md#statestyles) is set. Otherwise, the style settings will not take effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                 |
| ------ | ------- | ---- | ----------------------------------------------------- |
| value  | boolean | Yes  | Whether the grid item is selectable in the mouse selection box area. The **value** means that the grid item is selectable in the mouse selection box area, and **false** means the opposite.<br>Default value: **true**.|

### selected<sup>10+</sup>

selected(value: boolean)

Sets whether the grid item is selected. This attribute supports two-way binding through [$$](../../../ui/state-management/arkts-two-way-sync.md).

This attribute must be used before the [style for the selected state](./ts-universal-attributes-polymorphic-style.md#statestyles) is set. Otherwise, the style settings will not take effect.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                    |
| ------ | ------- | ---- | ---------------------------------------- |
| value  | boolean | Yes  | Whether the grid item is selected. The **value** means that the grid item is selected, and **false** means that the grid item is in the default state.<br>Default value: **false**.|

## GridItemOptions<sup>11+</sup>

Defines the style of a grid item.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name | Type                 | Mandatory| Description                        |
| ----- | -------------------- | ---- | ---------------------------- |
| style | [GridItemStyle](#griditemstyle11) | No  | Style of the grid item.<br>Default value: **GridItemStyle.NONE**.<br>If this parameter is set to **GridItemStyle.NONE**, no style is applied.<br>If this parameter is set to **GridItemStyle.PLAIN**, the grid item is in hover or press style depending on the state.|

## GridItemStyle<sup>11+</sup>

Enumerates styles of grid items.

**Atomic service API**: This API can be used in atomic services since API version 12.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name |Value| Description                  |
| ----- |----| ------------------------ |
| NONE  |  0 | No style.                |
| PLAIN |  1 | Hover or press style.|

> **NOTE**
>
> To set the focused style for the grid item, the grid container must have paddings of greater than 4 vp for accommodating the focus frame of the grid item.

## Events

### onSelect<sup>8+</sup>

onSelect(event: (isSelected: boolean) =&gt; void)

Triggered when the selected state of the grid item changes.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name    | Type   | Mandatory| Description                                                        |
| ---------- | ------- | ---- | ------------------------------------------------------------ |
| isSelected | boolean | Yes  | Returns **true** if the grid item is selected in the mouse selection box area; returns **false** otherwise.|

## Example

### Example 1: Setting the Grid Item Position
This example shows how to set the grid item position using **ColumnStart**, **ColumnEnd**, **RowStart**, and **RowEnd**. In situations where you need to designate the start row and column numbers as well as the number of rows and columns a grid item spans, you are advised to use the [layoutOptions parameter](ts-container-grid.md#gridlayoutoptions10) of the **Grid** component. For reference, see [Grid Example 1](ts-container-grid.md#example-1-creating-a-fixed-row-and-column-grid-layout) and [Grid Example 3](ts-container-grid.md#example-3-implementing-a-scrollable-grid-with-grid-items-spanning-rows-and-columns).

```ts
// xxx.ets
@Entry
@Component
struct GridItemExample {
  @State numbers: string[] = ["0", "1", "2", "3", "4", "5", "6", "7", "8", "9", "10", "11", "12", "13", "14", "15"];

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
        }.columnStart(1).columnEnd(4) // Set only the column numbers. The layout does not start from the first column.
      }
      .columnsTemplate('1fr 1fr 1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr 1fr 1fr 1fr')
      .width('90%').height(300)
    }.width('100%').margin({ top: 5 })
  }
}
```

![en-us_image_0000001174582870](figures/en-us_image_0000001174582870.gif)

### Example 2: Setting the Grid Item Style

This example shows how to set the grid item style using **GridItemOptions**.

```ts
// xxx.ets
@Entry
@Component
struct GridItemExample {
  @State numbers: String[] = ['0', '1', '2'];

  build() {
    Column({ space: 5 }) {
      Grid() {
        ForEach(this.numbers, (day: string) => {
          ForEach(this.numbers, (day: string) => {
            GridItem({style:GridItemStyle.NONE}) {
              Text(day)
                .fontSize(16)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
                .focusable(true)
            }
            .backgroundColor(0xF9CF93)
          }, (day: string) => day)
        }, (day: string) => day)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr')
      .columnsGap(4)
      .rowsGap(4)
      .width('60%')
      .backgroundColor(0xFAEEE0)
      .height(150)
      .padding('4vp')

      Grid() {
        ForEach(this.numbers, (day: string) => {
          ForEach(this.numbers, (day: string) => {
            GridItem({style:GridItemStyle.PLAIN}) {
              Text(day)
                .fontSize(16)
                .width('100%')
                .height('100%')
                .textAlign(TextAlign.Center)
                .focusable(true)
            }
            .backgroundColor(0xF9CF93)
          }, (day: string) => day)
        }, (day: string) => day)
      }
      .columnsTemplate('1fr 1fr 1fr')
      .rowsTemplate('1fr 1fr')
      .columnsGap(4)
      .rowsGap(4)
      .width('60%')
      .backgroundColor(0xFAEEE0)
      .height(150)
      .padding('4vp')
    }.width('100%').margin({ top: 5 })
  }
}
```

![en-us_image_griditem_griditemoptions](figures/en-us_image_griditem_griditemoptions.png)
