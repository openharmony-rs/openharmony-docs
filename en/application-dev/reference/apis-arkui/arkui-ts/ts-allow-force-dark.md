# Color Inversion

<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @fangzhiyuan1-->
<!--Designer: @fangzhiyuan1-->
<!--Tester: @gouyuanyuan-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=ca610c3b31eac2a84ffac21a107ce522b473feb1 translatedAt=2026-08-28T01:36:02.253Z pushedAt=2026-08-28T08:09:12.636Z -->

Sets whether to enable the color inversion for a component. The color inversion automatically inverts or transforms color values during dark/light mode switching. For details about the principle, see [Using Color Inversion for Quick Dark Mode Adaptation](../../../ui/ui-dark-light-color-adaptation.md#using-color-inversion-for-quick-dark-mode-adaptation). Developers can also proactively disable the color inversion to retain the original logic during dark/light mode switching.

>  **NOTE**
>
> - The initial APIs of this module are supported since API version 21. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.

## allowForceDark

allowForceDark(value: boolean): T

Sets whether to enable color inversion for the component.

> **NOTE**
>
> - When a component proactively disables the color inversion, the component and all its child components do not enable the color inversion, and are not affected by the invert color configuration of the parent component, ancestor components, or their own child components.
>
> - This API takes effect only when the color inversion is enabled. Calling this API to set the configuration when the color inversion is not enabled produces no effect. To enable the color inversion, see [Using Color Inversion for Quick Dark Mode Adaptation](../../../ui/ui-dark-light-color-adaptation.md#using-color-inversion-for-quick-dark-mode-adaptation).

**Atomic service API**: This API can be used in atomic services since API version 21.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name  | Type     | Mandatory| Description                      |
| ------ | -------- | -----|---------------------- |
| value  | boolean   |  Mandatory  | Whether the component is allowed to use the color inversion. The value **true** means that the component is allowed to use the color inversion, and **false** means the opposite. |

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component, used for chained calls. |

## Example

```ts
// After the allowForceDark(false) attribute is added to a component, the color inversion is not used for the current component and all its child components.
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
      .allowForceDark(false) // Column and its child component Text do not use the color inversion, and are not affected by the color inversion used by the parent component Column.

      Row() {
        Button('BUTTON')
          .backgroundColor(Color.Grey)
          .allowForceDark(true)
          .onClick(() => {
            console.info(`Button is clicked`);
          })
      }
      .allowForceDark(false) // Row and its child component Button do not use the color inversion, and are not affected by the color inversion used by the parent component Column.
    }
    .allowForceDark(true)
    .width('100%')
    .height('100%')
  }
}
```

![forceDark](./figures/force-dark.png)