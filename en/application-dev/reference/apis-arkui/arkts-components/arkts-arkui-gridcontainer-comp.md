# GridContainer

A vertical grid layout container, used only in grid layout scenarios. The grid layout implements responsive layout by dividing the container width into a specified number of columns, allowing child components to occupy different numbers of columns and offsets. It is suitable for responsive page layouts, multi-column content display, dashboard layouts, and other scenarios.

> **NOTE** > > This component is deprecated since API version 9. You are advised to use the new components > [GridCol](arkts-arkui-gridcol-comp.md#grid_col) and [GridRow](arkts-arkui-gridrow-comp.md#grid_row) instead. > > This component is supported since API version 7. New APIs added in later versions are marked with superscripts to > indicate their starting version.

## Child Components

Supported

## GridContainer

```TypeScript
GridContainer(value?: GridContainerOptions)
```

Creates a vertical grid layout container.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColInterface and grid_row/GridRowInterface

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GridContainerOptions](arkts-arkui-gridcontainer-comp-gridcontaineroptions-i.md) | No | Configuration parameter of **GridContainer**, used to set the number of columns, device width type, gutter, and margin of the grid layout. If not passed, the default configuration is used. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [GridContainerOptions](arkts-arkui-gridcontainer-comp-gridcontaineroptions-i.md) | Defines the grid layout container configuration parameter object, used to set the number of columns, device width type, gutter, and margin for the **GridContainer** component. |

### Enums

| Name | Description |
| --- | --- |
| [SizeType](arkts-arkui-gridcontainer-comp-sizetype-e.md) | Enumerates device width types, used to distinguish device types of different widths in the grid layout to implement responsive layout. |

## Examples

```TypeScript
// xxx.ets
// Grid Layout example: GridContainer with useSizeType for responsive layout
@Entry
@Component
struct GridContainerExample {
  @State sizeType: SizeType = SizeType.XS // Current device width type

  build() {
    Column({ space: 5 }) {
      // Configure a 12-column grid layout with 10 vp column spacing and 20 vp gutter.
      GridContainer({ columns: 12, sizeType: this.sizeType, gutter: 10, margin: 20 }) {
        Row() {
          // Child components use useSizeType to set span (number of columns occupied) and offset (number of columns offset) for different device width types.
          Text('1')
            .useSizeType({
              xs: { span: 6, offset: 0 },
              sm: { span: 2, offset: 0 },
              md: { span: 2, offset: 0 },
              lg: { span: 2, offset: 0 }
            })
            .height(50).backgroundColor(0x4682B4).textAlign(TextAlign.Center)
          Text('2')
            .useSizeType({
              xs: { span: 2, offset: 6 },
              sm: { span: 6, offset: 2 },
              md: { span: 2, offset: 2 },
              lg: { span: 2, offset: 2 }
            })
            .height(50).backgroundColor(0x00BFFF).textAlign(TextAlign.Center)
          Text('3')
            .useSizeType({
              xs: { span: 2, offset: 8 },
              sm: { span: 2, offset: 8 },
              md: { span: 6, offset: 4 },
              lg: { span: 2, offset: 4 }
            })
            .height(50).backgroundColor(0x4682B4).textAlign(TextAlign.Center)
          Text('4')
            .useSizeType({
              xs: { span: 2, offset: 10 },
              sm: { span: 2, offset: 10 },
              md: { span: 2, offset: 10 },
              lg: { span: 6, offset: 6 }
            })
            .height(50).backgroundColor(0x00BFFF).textAlign(TextAlign.Center)
        }
      }.width('90%')

      Text('Click Simulate to change the device width').fontSize(9).width('90%').fontColor(0xCCCCCC)
      // Click the button to switch the device width type and observe the responsive layout changes.
      Row() {
        Button('XS')
          .onClick(() => {
            this.sizeType = SizeType.XS
          }).backgroundColor(0x317aff)
        Button('SM')
          .onClick(() => {
            this.sizeType = SizeType.SM
          }).backgroundColor(0x317aff)
        Button('MD')
          .onClick(() => {
            this.sizeType = SizeType.MD
          }).backgroundColor(0x317aff)
        Button('LG')
          .onClick(() => {
            this.sizeType = SizeType.LG
          }).backgroundColor(0x317aff)
      }
    }.width('100%').margin({ top: 5 })
  }
}
```
