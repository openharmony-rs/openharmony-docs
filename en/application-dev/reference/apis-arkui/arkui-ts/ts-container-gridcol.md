# GridCol
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @fenglinbailu-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=45ec2d938cfede23d9ca90fe41c0d1f3e7b2b01d translatedAt=2026-11-17T03:59:05.117Z pushedAt=2026-11-19T08:20:04.865Z nl=1 -->

A column component in the grid layout system. It must be used as a child component of the grid container component ([GridRow](ts-container-gridrow.md)). It is suitable for responsive layout, multi-device adaptation, and other scenarios that require dynamic column width adjustment. It supports responsive breakpoint configuration, cross-column layout, offset, and sorting. Using the **GridCol** component enables quick implementation of responsive layouts, simplifying multi-device adaptation development.

>  **NOTE**
>
>  This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.  

## Child Components

This component can contain only one child component.
## APIs

GridCol(option?: GridColOptions)

Defines a grid column layout component. After creation, it participates in the layout calculation of the grid system as a child component of **GridRow**, based on the configured **span**, **offset**, and **order** attributes.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name| Type                                                 | Mandatory| Description                                                        |
| ------ | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| option   | [GridColOptions](#gridcoloptions) | No   | Configuration option for the grid layout child component, which can configure **span** (number of columns occupied), **offset** (number of columns offset), and **order** (sort sequence number). Pass this parameter when a custom grid layout behavior is needed, such as responsive column width, fixed offset position, or specified render order. It can be omitted when the default grid layout is used. If not passed, the default configuration is used. |

## GridColOptions

Defines the options of the **GridCol** component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| span   | number \| [GridColColumnOption](#gridcolcolumnoption) | No | Yes   | Number of columns occupied by the grid child component in the grid container component. A span of 0 indicates that the element does not participate in layout calculation and will not be rendered.<br>The value is a non-negative integer, and the default value is 1.<br>Invalid value: processed according to the default value.|
| offset | number \| [GridColColumnOption](#gridcolcolumnoption) | No | Yes   | Number of columns offset from the original position of the grid child component. An offset of 0 indicates no offset.<br>The value is a non-negative integer, and the default value is 0.<br>Invalid value: processed according to the default value.|
| order  | number \| [GridColColumnOption](#gridcolcolumnoption) | No | Yes   | Sequence number of the element. Sort grid child components in ascending order according to their sequence numbers.<br>The value is a non-negative integer, and the default value is 0.<br>Invalid value: processed according to the default value.<br>**Note:**<br>When child components do not set order or set the same order, they are displayed in code order.<br>When some child components set order and some do not, the child components without order are sorted first in sequence, and the child components with order are arranged in ascending order of their values.|

The values of `span`, `offset`, and `order` attributes are inherited in the sequence of **xs**, **sm**, **md**, **lg**, **xl**, and **xxl**. If no value is set for a breakpoint, the value is obtained from the previous breakpoint.

Since API version 20, the inheritance rules for `span` are described in [GridColColumnOption](#gridcolcolumnoption), while the inheritance rules for `offset` and `order` remain unchanged.

## Attributes
In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### span

span(value: number | GridColColumnOption)

Sets the number of columns occupied by the grid child component. After the call is successful, the grid child component occupies a grid area of the corresponding width based on the set column count. A span of **0** indicates that the element does not participate in layout calculation, meaning it will not be rendered.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type                                                        | Mandatory| Description                    |
| ------ | ------------------------------------------------------------ | ---- | ------------------------ |
| value  | number&nbsp;\|&nbsp;[GridColColumnOption](#gridcolcolumnoption) | Yes   | Number of columns occupied. If span is 0, it indicates that the element does not participate in layout calculation, that is, it will not be rendered.<br>The value is a non-negative integer, and the default value is **1**.<br>Invalid value: processed according to the default value.<br>**Note:** This attribute has breakpoint inheritance. For details, see [GridColOptions](#gridcoloptions). After API version 20, the default value inheritance rule changes. For details, see [GridColColumnOption](#gridcolcolumnoption). |

### gridColOffset

gridColOffset(value: number | GridColColumnOption)

Sets the number of columns by which the grid child component is offset relative to its original position.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type                                                        | Mandatory| Description                                            |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;[GridColColumnOption](#gridcolcolumnoption) | Yes   | Number of columns offset from the original position. **gridColOffset** being 0 indicates no offset.<br>The value is a non-negative integer, and the default value is **0**.<br>Invalid value: processed according to the default value.<br>**Note:** This attribute has breakpoint inheritance. For details, see [GridColOptions](#gridcoloptions).|

### order

order(value: number | GridColColumnOption)

Sets the display order of the grid child component. Grid child components are sorted in ascending order based on their sequence numbers.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters** 

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number&nbsp;\|&nbsp;[GridColColumnOption](#gridcolcolumnoption) | Yes   | Element sequence number, sorted in ascending order according to the sequence numbers of grid child components.<br>The value is a non-negative integer, and the default value is **0**.<br>Invalid value: processed according to the default value.<br>**Note:** This attribute has breakpoint inheritance. For details, see [GridColOptions](#gridcoloptions).|

## GridColColumnOption

Describes the numbers of grid columns occupied by the **GridCol** component on devices with different width types.

- In versions earlier than API version 20: When you configure **GridCol** column spans only at specific breakpoints, unconfigured breakpoints inherit values from the next smaller configured breakpoint. If no smaller breakpoint is configured, the default value of **1** is used.
  <!--code_no_check-->
  ```ts
  span: {xs:2, md:4, lg:8} // Equivalent to span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
  span: {md:4, lg:8} // Equivalent to span: {xs:1, sm:1, md:4, lg:8, xl:8, xxl:8}.
  ```
- Since API version 20: When you configure **GridCol** column spans only at specific breakpoints, unconfigured breakpoints inherit values from the next smaller configured breakpoint. If no smaller breakpoint exists, values are inherited from the next larger configured breakpoint.
  <!--code_no_check-->
  ```ts
  span: {xs:2, md:4, lg:8} // Equivalent to span: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
  span: {md:4, lg:8} // Equivalent to span: {xs:4, sm:4, md:4, lg:8, xl:8, xxl:8}.
  ```
- Recommendation: Explicitly configure **GridCol** column spans for all required breakpoints to prevent unexpected layout behavior caused by automatic value inheritance.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| xs  | number | No | Yes | Number of grid columns occupied by the grid child component on a minimum-width device. The value is a non-negative integer. The default value is 1. Invalid value: processed according to the default value. |
| sm  | number | No | Yes | Number of grid columns occupied by the grid child component on a small-width device. The value is a non-negative integer. The default value is 1. Invalid value: processed according to the default value. |
| md  | number | No | Yes | Number of grid columns occupied by the grid child component on a medium-width device. The value is a non-negative integer. The default value is 1. Invalid value: processed according to the default value. |
| lg  | number | No | Yes | Number of grid columns occupied by the grid child component on a large-width device. The value is a non-negative integer. The default value is 1. Invalid value: processed according to the default value. |
| xl  | number | No | Yes | Number of grid columns occupied by the grid child component on an extra-large-width device. The value is a non-negative integer. The default value is 1. Invalid value: processed according to the default value. |
| xxl | number | No | Yes | Number of grid columns occupied by the grid child component on an extra-extra-large-width device. The value is a non-negative integer. The default value is 1. Invalid value: processed according to the default value. |

## Events
The [universal events](ts-component-general-events.md) are supported.

## Example
This example demonstrates the basic usage of **GridCol**.

```ts
// xxx.ets
@Entry
@Component
struct GridColExample {
  @State bgColors: Color[] =
    [Color.Red, Color.Orange, Color.Yellow, Color.Green, Color.Pink, Color.Grey, Color.Blue, Color.Brown]
  @State currentBp: string = 'unknown'

  build() {
    Column() {
      // Create a grid container, and configure the number of columns, spacing, and responsive breakpoints.
      GridRow({
        columns: 5,
        gutter: { x: 5, y: 10 },
        // Set responsive breakpoints based on the window size.
        breakpoints: {
          value: ['400vp', '600vp', '800vp'],
          reference: BreakpointsReference.WindowSize
        },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          // Configure the span value at different breakpoints to implement responsive layout.
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

![figures/gridrow.png](figures/gridrow.png)