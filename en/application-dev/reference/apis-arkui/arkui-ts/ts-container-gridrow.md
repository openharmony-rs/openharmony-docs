# GridRow
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @zju_ljz-->
<!--Designer: @lanshouren-->
<!--Tester: @liuli0427-->
<!--Adviser: @Brilliantry_Rui-->

The responsive grid layout provides rules for layout design and resolves issues of dynamic layout across devices with different sizes, thereby ensuring layout consistency across layouts on different devices.

The **GridRow** component is used in a grid layout, together with its child component [GridCol](ts-container-gridcol.md).

>  **NOTE**
>
> This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

This component can contain the **GridCol** child component.


## APIs
GridRow(option?: GridRowOptions)

Creates a **GridRow** container.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name|Type|Mandatory|Description|
|-----|-----|----|----|
| option | [GridRowOptions](#gridrowoptions) | No | Child component options of the grid layout.|

## GridRowOptions

Defines layout options of the **GridRow** container.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
|columns| number \| [GridRowColumnOption](#gridrowcolumnoption) |  No| Yes |Number of columns in the grid layout.<br>The value is an integer greater than 0.<br>- Before API version 20: The default value is 12.<br>- API version 20 or later: The default value is { xs: 2, sm: 4, md: 8, lg: 12, xl: 12, xxl: 12 }.<br>Invalid values are treated as the default value.|
|gutter|[Length](ts-types.md#length) \| [GutterOption](#gutteroption)|  No| Yes |Gutter of the grid layout.<br>Default value: **0**<br>Invalid values are treated as the default value.<br>Unit: vp.|
|breakpoints|[BreakPoints](#breakpoints)|  No| Yes |Breakpoint values and the corresponding reference based on the application window or container size.<br>Default value:<br>{<br>value: ["320vp", "600vp", "840vp"],<br>reference: BreakpointsReference.WindowSize<br>} <br>Invalid values are treated as the default value.<br>Unit: vp.|
|direction|[GridRowDirection](#gridrowdirection)|  No| Yes |Arrangement direction of the grid layout.<br>Default value: **GridRowDirection.Row**<br>Invalid values are treated as the default value.|

## GutterOption

Provides the gutter options for the grid layout to define the spacing between child components in different directions.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| x  | [Length](ts-types.md#length) \| [GridRowSizeOption](#gridrowsizeoption) | No | Yes | Horizontal spacing between grid child components.   |
| y  | [Length](ts-types.md#length) \| [GridRowSizeOption](#gridrowsizeoption) | No | Yes  | Vertical spacing between grid child components.   |

## GridRowColumnOption

Describes the numbers of grid columns for devices with different grid sizes.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| xs  | number | No  | Yes  | Number of grid columns on the device where the grid size is xs.   |
| sm  | number | No   | Yes | Number of grid columns on the device where the grid size is sm.     |
| md  | number | No   | Yes | Number of grid columns on the device where the grid size is md.   |
| lg  | number | No  | Yes  | Number of grid columns on the device where the grid size is lg.     |
| xl  | number | No   | Yes | Number of grid columns on the device where the grid size is xl.   |
| xxl | number | No   | Yes | Number of grid columns on the device where the grid size is xxl.   |

**NOTE**
- In versions earlier than API version 20: When **GridRow** column spans are configured only at specific breakpoints, unconfigured breakpoints inherit values from the next smaller configured breakpoint. If no smaller breakpoint exists, the default column count (12) is used for unconfigured breakpoints.
  <!--code_no_check-->
  ```ts
  columns: {xs:2, md:4, lg:8} // Equivalent to columns: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
  columns: {md:4, lg:8} // Equivalent to columns: {xs:12, sm:12, md:4, lg:8, xl:8, xxl:8}.
  ```
- Since API version 20: When **GridRow** column spans are configured only at specific breakpoints, unconfigured breakpoints inherit values from the next smaller configured breakpoint. If no smaller breakpoint exists, values are inherited from the next larger configured breakpoint.
  <!--code_no_check-->
  ```ts
  columns: {xs:2, md:4, lg:8} // Equivalent to columns: {xs:2, sm:2, md:4, lg:8, xl:8, xxl:8}.
  columns: {md:4, lg:8} // Equivalent to columns: {xs:4, sm:4, md:4, lg:8, xl:8, xxl:8}.
  ```
- Recommendation: Explicitly configure **GridRow** column spans for all required breakpoints to prevent unexpected layout behavior caused by automatic value inheritance.
- The width of each column is the content area size of the **GridRow** component minus the gutter of the grid child components, and then divided by the total number of columns. For example, if columns is set to 12, gutter is set to 10px, and padding is set to 20px for a GridRow with a width of 800px, the width of each column is (800 – 20 x 2 – 10 x 11)/12.

## GridRowSizeOption

Describes the gutter sizes for different device width types.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| xs  | [Length](ts-types.md#length) | No | Yes  | Gutter size for minimum device width.   |
| sm  | [Length](ts-types.md#length) | No | Yes  | Gutter size for small device width.     |
| md  | [Length](ts-types.md#length) | No | Yes  | Gutter size for medium device width.   |
| lg  | [Length](ts-types.md#length) | No | Yes  | Gutter size for large device width.     |
| xl  | [Length](ts-types.md#length) | No | Yes  | Gutter size for extra large device width.   |
| xxl | [Length](ts-types.md#length) | No | Yes  | Gutter size for extra extra large device width.   |

## BreakPoints

Sets breakpoints for the responsive grid container. For details about breakpoints, see [Breakpoints](../../../ui/arkts-layout-development-grid-layout.md#breakpoints).

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| value  | Array&lt;string&gt; | No| Yes | Array of monotonically increasing breakpoints.<br>Default value: **["320vp", "600vp", "840vp"]**<br>Invalid values are treated as the default value.<br>Unit: vp.   |
| reference  | [BreakpointsReference](#breakpointsreference) | No| Yes  | Breakpoint switching reference.<br>Default value: **BreakpointsReference.WindowSize**<br>Invalid values are treated as the default value.|
<!--code_no_check-->
```ts
  // Enable the xs, sm, and md breakpoints.
  breakpoints: {value: ["100vp", "200vp"]}
  // Enable four breakpoints: xs, sm, md, and lg. The breakpoint range must be monotonically increasing.
  breakpoints: {value: ["320vp", "600vp", "840vp"]}
  // Enable five breakpoints: xs, sm, md, lg, and xl. The number of breakpoint ranges cannot exceed the number of breakpoints minus 1.
  breakpoints: {value: ["320vp", "600vp", "840vp", "1080vp"]}
```

## BreakpointsReference

Breakpoint reference of the grid container component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Description|
| -------- | -------- |
| WindowSize | The window is used as a reference.|
| ComponentSize | The container is used as a reference.|

## GridRowDirection

Grid element arrangement direction.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Description|
| -------- | -------- |
| Row | Grid elements are arranged in the row direction.|
| RowReverse | Grid elements are arranged in the reverse row direction.|

**NOTE**
* Grid elements can be arranged only in the **Row** or **RowReverse** direction, but not in the **Column** or **ColumnReverse** direction.
* The location and size of a grid child component can be calculated only based on **span** and **offset**. If the **span** values of child components add up to a number greater than the allowed number of columns, the grid will automatically wrap lines.
* If the **span** value of a single child component exceeds the maximum number of columns, the maximum number of columns is used.
* If a child component takes up more than the total number of columns according to its **offset** and **span** settings, it will be placed in a new row.
* Example: Item1: GridCol({ span: 6 }), Item2: GridCol({ span: 8, offset:11 }) 

|1      | 2     | 3     | 4     | 5     | 6     | 7     | 8     | 9     | 10    | 11    | 12    |
| ----- | ------ | ---- | ---- | -----|-----|---------|--------|------|------- |------- |------- |
| $\circ$ | $\circ$ | $\circ$ | $\circ$ | $\circ$|$\circ$| - |  - |  - |  -  | -  | -  |
| -     | -     | -     | -     | -     |       |       |       |       |       |   |   |
| $\circ$ | $\circ$ | $\circ$ | $\circ$ | $\circ$|$\circ$|$\circ$|$\circ$|  |   |   |   |

## Attributes

In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### alignItems<sup>10+</sup>

alignItems(value: ItemAlign)

Sets the alignment mode of the **GridCol** components along the vertical main axis of the **GridRow** component. The alignment mode of the **GridCol** component can also be set using **alignSelf([ItemAlign](ts-appendix-enums.md#itemalign))**. If both of the preceding methods are used, the setting of **alignSelf(ItemAlign)** prevails.

**Widget capability**: This API can be used in ArkTS widgets since API version 10.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                       | Mandatory| Description                                                        |
| ------ | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [ItemAlign](ts-appendix-enums.md#itemalign) | Yes  | Alignment mode of the **GridCol** components along the vertical main axis of the **GridRow** component.<br>Default value: **ItemAlign.Start**<br>Invalid values are treated as the default value.<br>**NOTE**<br>**ItemAlign** supports the following enums: **ItemAlign.Start**, **ItemAlign.Center**, **ItemAlign.End**, and **ItemAlign.Stretch**.|


## Events

In addition to the [universal events](ts-component-general-events.md), the following events are supported.

### onBreakpointChange

onBreakpointChange(callback: (breakpoints: string) => void)

Triggered when the breakpoint changes.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type  | Mandatory  | Description  |
| ----- | ------ | ---- | ---------------------------------------- |
|callback| (breakpoints: string) => void |Yes|Breakpoints can be xs, sm, md, lg, xl, or xxl.|

## Example

This example shows the basic usage of the responsive grid layout.

```ts
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
        breakpoints: { value: ["400vp", "600vp", "800vp"],
          reference: BreakpointsReference.WindowSize },
        direction: GridRowDirection.Row
      }) {
        ForEach(this.bgColors, (color: Color) => {
          GridCol({ span: { xs: 1, sm: 2, md: 3, lg: 4 }, offset: 0, order: 0 }) {
            Row().width("100%").height("20vp")
          }.borderColor(color).borderWidth(2)
        })
      }.width("100%").height("100%")
      .onBreakpointChange((breakpoint) => {
        this.currentBp = breakpoint
      })
    }.width('80%').margin({ left: 10, top: 5, bottom: 5 }).height(200)
    .border({ color: '#880606', width: 2 })
  }
}
```

![figures/gridrow.png](figures/gridrow.png)
