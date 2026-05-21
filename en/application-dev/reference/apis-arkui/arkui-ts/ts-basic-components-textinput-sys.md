# TextInput (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **TextInput** component provides single-line text input.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [TextInput](ts-basic-components-textinput.md).

## InputType

Sets the single-line text input box type.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

| Name                                | Value| Description                                      |
| ---------------------------------- | --- | ---------------------------------------- |
| SCREEN_LOCK_PASSWORD<sup>11+</sup> | 9 | Lock screen password input mode. This mode accepts only digits, letters, underscores (_), spaces, and special characters. An eye icon is used to show or hide the password, and the entered text is hidden behind dots by default. Since API version 12, on specific devices, the entered text is displayed directly as dots. The password input mode does not support underlines.<br>**System API**: This is a system API.|

## voiceButton<sup>23+</sup>

voiceButton(options: Optional\<VoiceButtonOptions\>)

Sets the voice button options.

**System API**: This is a system API.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 23.

**Parameters**

| Name| Type| Mandatory| Description|
| ----- | ----- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt)<[VoiceButtonOptions](./ts-text-common-sys.md#voicebuttonoptions23)> | Yes | Voice button options.|


## Examples

### Example 1: Setting a Voice Button

This example demonstrates how to enable the voice button for an input box by configuring the **voiceButton** API.

The [voiceButton](#voicebutton23) API is added since API version 23.

```ts
// xxx.ets
@Entry
@Component
struct TextInputxample {

  build() {
    Column() {
      TextInput().voiceButton({enabled: true})
    }
  }
}
```
