# GridCol

The **GridCol** component must be used as a child component of the [GridRow](ts-container-gridrow.md) container.

>  **NOTE**
>
> This component is supported since API version 9. Updates will be marked with a superscript to indicate their earliest API version. 

## Child Components

This component can contain only one child component.
## APIs

GridCol(option?: GridColOptions)

Creates a **GridCol** component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**
| Name| Type                                                 | Mandatory| Description                                                        |
| ------ | ----------------------------------------------------- | ---- | ------------------------------------------------------------ |
| option   | [GridColOptions](#gridcoloptions) | No  | Options of the **GridCol** component.|

## GridColOptions

Defines the options of the **GridCol** component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| span   | number \| [GridColColumnOption](#gridcolcolumnoption) | No| Yes  | Number of columns occupied by the component. If it is set to **0**, the component is not involved in layout calculation, that is, the component is not rendered.<br>The value must be a non-negative integer. Default value: **1**.<br>Invalid values are treated as the default value.|
| offset | number \| [GridColColumnOption](#gridcolcolumnoption) | No| Yes  | Number of offset columns relative to the original position of the component.<br>The value must be a non-negative integer. Default value: **0**.<br>Invalid values are treated as the default value.|
| order  | number \| [GridColColumnOption](#gridcolcolumnoption) | No| Yes  | Sequence number of the component. Child components of the grid are sorted in ascending order based on their sequence numbers.<br>The value must be a non-negative integer. Default value: **0**.<br>Invalid values are treated as the default value.<br>**NOTE**<br>If a child component shares an **order** value with another child component or does not have **order** set, it is displayed based on its code sequence number.<br>If **order** is not set for all child components, those that have **order** set are displayed after those that do not and are sorted in ascending order based on the value.|

The values of `span`, `offset`, and `order` attributes are inherited in the sequence of **xs**, **sm**, **md**, **lg**, **xl**, and **xxl**. If no value is set for a breakpoint, the value is obtained from the previous breakpoint.

## Attributes
In addition to the [universal attributes](ts-component-general-attributes.md), the following attributes are supported.

### span

span(value: number | GridColColumnOption)

Sets the number of columns occupied by the component. If it is set to **0**, the element is not involved in layout calculation, that is, the element is not rendered.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                    |
| ------ | ------------------------------------------------------------ | ---- | ------------------------ |
| value  | number \| [GridColColumnOption](#gridcolcolumnoption) | Yes  | Number of occupied columns.<br>The value must be a non-negative integer. Default value: **1**.<br>Invalid values are treated as the default value.|

### gridColOffset

gridColOffset(value: number | GridColColumnOption)

Sets the number of offset columns relative to the original position of the component.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                            |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| value  | number \| [GridColColumnOption](#gridcolcolumnoption) | Yes  | Number of offset columns relative to the previous child component of the grid<br>The value must be a non-negative integer. Default value: **0**.<br>Invalid values are treated as the default value.|

### order

order(value: number | GridColColumnOption)

Sets the display order of the grid child component. Grid child components are sorted in ascending order based on their sequence numbers.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                                                        | Mandatory| Description                                                        |
| ------ | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| value  | number \| [GridColColumnOption](#gridcolcolumnoption) | Yes  | Sequence number of the component. Child components of the grid are sorted in ascending order based on their sequence numbers.<br>The value must be a non-negative integer. Default value: **0**.<br>Invalid values are treated as the default value.|

## GridColColumnOption

Describes the numbers of grid columns occupied by the **GridCol** component on devices with different width types.

**Widget capability**: This API can be used in ArkTS widgets since API version 9.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| xs  | number | No| Yes | Number of grid columns on the device where the grid size is xs.   |
| sm  | number | No| Yes | Number of grid columns on the device where the grid size is sm.     |
| md  | number | No| Yes | Number of grid columns on the device where the grid size is md.   |
| lg  | number | No| Yes | Number of grid columns on the device where the grid size is lg.     |
| xl  | number | No| Yes | Number of grid columns on the device where the grid size is xl.   |
| xxl | number | No| Yes | Number of grid columns on the device where the grid size is xxl.   |

## Events
The [universal events](ts-component-general-events.md) are supported.

## Example
See the example for [GridRow](ts-container-gridrow.md#example).
