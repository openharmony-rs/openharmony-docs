# Enable/Disable Control
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiangtao92-->
<!--Designer: @piggyguy-->
<!--Tester: @songyanhong-->
<!--Adviser: @Brilliantry_Rui-->

You can enable or disable a component to control whether it responds to user interactions. When a component is enabled, it can respond to the following events: [click event](ts-universal-events-click.md), [touch event](ts-universal-events-touch.md), [drag event](ts-universal-events-drag-drop.md), [key event](ts-universal-events-key.md), [focus event](ts-universal-focus-event.md), [mouse event](ts-universal-mouse-key.md), [axis event](ts-universal-events-axis.md), [hover event](ts-universal-events-hover.md), [accessibility hover event](ts-universal-accessibility-hover-event.md), [gesture event](ts-gesture-settings.md), [focus axis event](ts-universal-events-focus_axis.md), and [crown event](ts-universal-events-crown.md).

>  **NOTE**
>
>  The initial APIs of this module are supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
>  The **enabled** attribute takes effect only when the component is pressed. Changes to it during interaction will not be applied.

## enabled

enabled(value: boolean): T

Sets whether the component responds to user interactions. If **enabled** is not set, the component responds to user interactions by default.

**Widget capability**: Since API version 9, this feature is supported in ArkTS widgets.

**Atomic service API**: This API can be used in atomic services since API version 11.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Parameters**

| Name| Type   | Mandatory| Description                                                        |
| ------ | ------- | ---- | ------------------------------------------------------------ |
| value  | boolean | Yes  | Whether the component responds to user interactions, including clicks and touches. The value **true** means that the component responds to user interactions,<br>and **false** means the opposite.|

**Return value**

| Type| Description|
| -------- | -------- |
| T | Current component.|

## Example

This example demonstrates how to use **enabled** to set whether a button responds to user interactions.

```ts
// xxx.ets
@Entry
@Component
struct EnabledExample {

  build() {
    Flex({ justifyContent: FlexAlign.SpaceAround }) {
      // The button does not respond to clicks.
      Button('disable').enabled(false).backgroundColor(0x317aff).opacity(0.4)
      Button('enable').backgroundColor(0x317aff)
    }
    .width('100%')
    .padding({ top: 5 })
  }
}
```

![en-us_image_0000001212218428](figures/en-us_image_0000001212218428.gif)
