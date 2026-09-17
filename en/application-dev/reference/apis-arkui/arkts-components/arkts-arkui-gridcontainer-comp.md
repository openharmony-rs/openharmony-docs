# GridContainer

Defines GridContainer Component.

## GridContainer

```TypeScript
GridContainer(value?: GridContainerOptions)
```

Defines the constructor of GridContainer.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** grid_col/GridColInterface and grid_row/GridRowInterface

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [GridContainerOptions](arkts-arkui-gridcontaineroptions-i.md) | No |  |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [GridContainerOptions](arkts-arkui-gridcontaineroptions-i.md) | Defines the options of GridContainer. |

### Enums

| Name | Description |
| --- | --- |
| [SizeType](arkts-arkui-sizetype-e.md) | Defines the size type. |

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
