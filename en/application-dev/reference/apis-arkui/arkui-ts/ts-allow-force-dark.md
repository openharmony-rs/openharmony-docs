# Color Inversion
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @lushi871202-->
<!--Designer: @demon_coffee-->
<!--Tester: @demon_coffee-->
<!--Adviser: @Brilliantry_Rui-->

You can specify whether to enable the color inversion feature for a component. This feature automatically inverts or modifies color values during color mode (dark/light) transitions. You can disable the color inversion algorithm to maintain original color behavior during color mode transitions.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## allowForceDark

allowForceDark(value: boolean): T

Sets whether to enable color inversion for the component.

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type     | Mandatory| Description                      |
| ------ | -------- | -----|---------------------- |
| value  | boolean   |  Yes | Whether to enable color inversion. **true** to enable, **false** otherwise.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

> **NOTE**
>
> When a component has color inversion disabled, both the component and all its child components will ignore color inversion capabilities, regardless of the settings on parent or ancestor components.

## Example

```ts
// Components with allowForceDark(false) will ignore color inversion capabilities.
@Entry
@Component
struct ComponentPage {
  build() {
    Column() {
      Column() {
        Text("Hello World")
          .fontSize(20)
          .fontColor(Color.Blue)
          .onClick(() => {
            console.info(`Text is clicked`);
          })
      }
      .allowForceDark(false) // Disable color inversion for Column and its child Text component, ignoring the color inversion settings of the parent component Column.

      Row() {
        Button('BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Disable color inversion for Row and its child Button component, ignoring the color inversion settings of the parent component Column.
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```
![forceDark](./figures/force-dark.png)
