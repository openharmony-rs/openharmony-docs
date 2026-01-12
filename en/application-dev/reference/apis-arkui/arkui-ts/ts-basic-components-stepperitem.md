# StepperItem
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @mayaolll-->
<!--Designer: @jiangdayuan-->
<!--Tester: @Giacinta-->
<!--Adviser: @Brilliantry_Rui-->

The **StepperItem** component represents a page component used within a [Stepper](ts-basic-components-stepper.md) container.


>  **NOTE**
> 
> This component is deprecated since API version 22. You are advised to use [Swiper](ts-container-swiper.md) instead.
>
>  This component is supported since API version 8. Updates will be marked with a superscript to indicate their earliest API version.


## Child Components

This component supports only one child component.


## APIs

StepperItem()

Creates a page component for the [Stepper](ts-basic-components-stepper.md) container.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

## Attributes

### prevLabel

prevLabel(value: string)

Sets the text label of the button on the left, which is not displayed on the first page. When the **Stepper** contains more than one page, the default value for all pages except the first page is **Back**.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | string | Yes| Text label of the button on the left. When the string is too long, it is scaled down, wrapped in two lines, and then clipped.|

### nextLabel

nextLabel(value: string)

Sets the text label of the button on the right. The default value is **Start** for the last page and **Next** for the other pages.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                           | Mandatory| Description                                                        |
| ------ | ------------------------------- | ---- | ------------------------------------------------------------ |
| value  | string                          | Yes  | Text label of the button on the right. When the string is too long, it is scaled down, wrapped in two lines, and then clipped.                       |

### status

status(value?: ItemState)

Sets the display status of **nextLabel** in the stepper.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type                           | Mandatory| Description                                                        |
| ------ | ------------------------------- | ---- | ------------------------------------------------------------ |
| value  | [ItemState](#itemstate) | No  | Display status of **nextLabel** in the stepper.<br>Default value: **ItemState.Normal**|

>  **NOTE**
>
>  - The **StepperItem** component does not support setting of the universal width attribute. By default, its width is the same as that of the parent **Stepper** component.
>  - The **StepperItem** component does not support setting of the universal height attribute. Its height is the height of the parent **Stepper** component minus the height of the label button.
>  - The **StepperItem** component does not support setting of the **aspectRadio** or **constrainSize** attribute, which may affect the length and width.
## ItemState

Display status of **nextLabel** in the stepper.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

|   Name   | Value| Description|
| -------- |-------- |-------- |
| Normal | 0 |The button on the right is clickable and can navigate users to the next **StepperItem** when it is clicked.|
| Disabled | 1 |The button on the right is disabled.|
| Waiting | 2 | The button on the right is not displayed, and a progress bar is displayed instead.|
| Skip | 3 | The button on the right reads "Skip" by default. You can define the processing logic for this state in the **onSkip** callback of the stepper.|


## Example

See [Stepper](ts-basic-components-stepper.md).
