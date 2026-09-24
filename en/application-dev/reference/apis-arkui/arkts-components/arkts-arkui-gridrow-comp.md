# GridRow

The responsive grid layout provides rules for layout design and resolves issues of dynamic layout across devices with different sizes, thereby ensuring layout consistency across layouts on different devices.

The **GridRow** component is used in a grid layout, together with its child component [GridCol](arkts-arkui-gridcol-comp.md#grid_col).

It supports dynamically adjusting the number of columns and gutter sizes based on device sizes and breakpoints to implement responsive layout.

## Child Components

This component can contain the **GridCol** child component.

## GridRow

```TypeScript
GridRow(option?: GridRowOptions)
```

Defines a grid row layout container. It can only be used with grid child components in grid layout scenarios.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [GridRowOptions](arkts-arkui-gridrow-comp-gridrowoptions-i.md) | No | Layout options of the grid row layout container. This parameter is passed when you need to customize the grid layout (such as setting the number of columns, gutter, breakpoint positions, and arrangement direction). If not passed, the default configuration is used. **GridRow** must be used together with [GridCol](arkts-arkui-gridcol-comp.md#grid_col) child components. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [BreakPoints](arkts-arkui-gridrow-comp-breakpoints-i.md) | Sets breakpoints for the responsive grid container. For details about breakpoints, see [Breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints). |
| [GridRowColumnOption](arkts-arkui-gridrow-comp-gridrowcolumnoption-i.md) | Describes the grid column number configuration for different device width types. |
| [GridRowOptions](arkts-arkui-gridrow-comp-gridrowoptions-i.md) | Defines layout options of the **GridRow** container. |
| [GridRowSizeOption](arkts-arkui-gridrow-comp-gridrowsizeoption-i.md) | Describes the gutter sizes for different device width types. |
| [GutterOption](arkts-arkui-gridrow-comp-gutteroption-i.md) | Provides the gutter options for the grid layout to define the spacing between child components in different directions. |

### Enums

| Name | Description |
| --- | --- |
| [BreakpointsReference](arkts-arkui-gridrow-comp-breakpointsreference-e.md) | Breakpoint reference of the grid container component. |
| [GridRowDirection](arkts-arkui-gridrow-comp-gridrowdirection-e.md) | Grid element arrangement direction. |

## Examples

### Example 1: Basic Usage of Grid Layout

This example demonstrates the basic usage of the GridRow component.



```TypeScript
// xxx.ets
@Entry
@Component
struct GridRowExample {
  @State bgColors: Color[] = [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink, Color.Grey, Color.Blue, Color.Brown]
  @State currentBp: string = 'unknown'

  build() {
    Column() {
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
        breakpoints: { value: ['400vp', '600vp', '800vp'],
          reference: BreakpointsReference.WindowSize },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          GridCol({ span: { xs: 1, sm: 2, md: 3, lg: 4 }, offset: 0, order: 0 }) {
            Row().width('100%').height('20vp')
          }.borderColor(color).borderWidth(2)
        })
      }.width('100%').height('100%')
      .onBreakpointChange((breakpoint) => {
        this.currentBp = breakpoint
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 }).height(200)
    .border({ color: '#880606', width: 2 })
  }
}
```

### Example 2: Basic Usage of AlignItems

This example demonstrates the effect of the GridCol component in different alignItems alignment modes.

```TypeScript
@ComponentV2
struct AlignItemsDemo {
  bgColors: Color[] = [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink];
  @Param alignment: ItemAlign = ItemAlign.Start; // Receive the alignItems attribute value passed from the parent component.

  ToString(alignment: ItemAlign): string {
    switch (alignment) {
      case ItemAlign.Start:
        return 'ItemAlign.Start';
      case ItemAlign.Center:
        return 'ItemAlign.Center';
      case ItemAlign.End:
        return 'ItemAlign.End';
      case ItemAlign.Stretch:
        return 'ItemAlign.Stretch';
      default:
        return 'ItemAlign.Auto';
    }
  }

  build() {
    Column() {
      Text(this.ToString(this.alignment))
        .fontSize(9)
        .fontColor(0xCCCCCC)
        .width('90%')
        .alignSelf(ItemAlign.Start)
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
      }) {
        ForEach(this.bgColors, (color: Color, index: number) => {
          GridCol({ span: 1 }) {
            Row() {
            }.width('100%').height(`${(index + 1) * 20}%`) // Set different heights for the Row in GridCol to observe the effect of the alignItems attribute.
          }.borderColor(color).borderWidth(2)
        })
      }
      .border({ color: '#880606', width: 2 })
      .alignItems(this.alignment)
      .width('100%')
    }
    .height('20%')
  }
}

@Entry
@ComponentV2
struct GridRowExample {
  alignmentArray: ItemAlign[] = [ItemAlign.Start, ItemAlign.Center, ItemAlign.End, ItemAlign.Stretch];

  build() {
    Column({ space: 15 }) {
      ForEach(this.alignmentArray, (ele: ItemAlign) => {
        AlignItemsDemo({ alignment: ele })
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 }).height('100%')
  }
}
```
