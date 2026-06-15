# Color Inversion
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->

You can specify whether to enable the color inversion feature for a component. This feature automatically inverts or modifies color values during color mode (dark/light) transitions. You can disable the color inversion algorithm to maintain original color behavior during color mode transitions.

>  **NOTE**
>
> The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## allowForceDark

allowForceDark(value: boolean): T

Sets whether to enable color inversion for the component.

> **NOTE**
>
> - When color inversion is disabled on a component, this feature remains inactive for the component and all its child components, regardless of the color inversion configuration of the parent, ancestor, and child components.
>
> - This API takes effect only when color inversion is enabled. For details about how to enable color inversion, see [Using Color Inversion for Quick Dark Mode Adaptation](../../../ui/ui-dark-light-color-adaptation.md#using-color-inversion-for-quick-dark-mode-adaptation).

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
