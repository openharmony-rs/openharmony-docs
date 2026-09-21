# GridCol

A column component in the grid layout system. It must be used as a child component of the grid container component ([GridRow](arkts-arkui-gridrow-comp.md#grid_row)). It is suitable for responsive layout, multi-device adaptation, and other scenarios that require dynamic column width adjustment. It supports responsive breakpoint configuration, cross-column layout, offset, and sorting. Using the **GridCol** component enables quick implementation of responsive layouts, simplifying multi-device adaptation development.

## Child Components

This component can contain only one child component.

## GridCol

```TypeScript
GridCol(option?: GridColOptions)
```

Defines a grid column layout component. After creation, it participates in the layout calculation of the grid system as a child component of **GridRow**, based on the configured **span**, **offset**, and **order** attributes.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| option | [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md) | No | Configuration options for the grid layout child component, which can be used to configure **span** (number of occupied columns), **offset** (number of offset columns), and **order** (sorting sequence). Pass this parameter when custom grid layout behavior is required (such as responsive column width, fixed offset position, and specified rendering order). This parameter can be omitted when the default grid layout is used. The default configuration is used when this parameter is not passed. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [GridColColumnOption](arkts-arkui-gridcol-comp-gridcolcolumnoption-i.md) | Describes the numbers of grid columns occupied by the **GridCol** component on devices with different width types. |
| [GridColOptions](arkts-arkui-gridcol-comp-gridcoloptions-i.md) | Defines the options of the **GridCol** component. |

## Examples

This example demonstrates the basic usage of GridCol.

```TypeScript
// xxx.ets
@Entry
@Component
struct GridColExample {
  @State bgColors: Color[] =
    [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink, Color.Grey, Color.Blue, Color.Brown]
  @State currentBp: string = 'unknown'

  build() {
    Column() {
      // Create the grid container, configure the column count, spacing, and responsive breakpoints.
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
        // Set the responsive breakpoints based on window size.
        breakpoints: {
          value: ['400vp', '600vp', '800vp'],
          reference: BreakpointsReference.WindowSize
        },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          // Configure span values at different breakpoints to implement responsive layout.
          GridCol({
            span: { xs: 1, sm: 2, md: 3, lg: 4 },
            offset: 0,
            order: 0
          }) {
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
