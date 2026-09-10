# TextInput (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-09-03T12:41:29.196Z -->

A single-line text input component that receives single-line text entered by the user. It supports multiple input types, such as password and voice, and can be used in scenarios such as form filling, search boxes, and login and registration, helping developers quickly build user interaction interfaces.

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
| SCREEN_LOCK_PASSWORD<sup>11+</sup> | 9 | Lock screen application password input mode. Supports input of digits, letters, underscores, spaces, and special characters. The password displays a small eye icon and the text is converted to dots by default. Since API version 12, text entered on Wearable devices is directly displayed as dots. The password input mode does not support the underline style. <br>**System API:** This is a system API.<br>**Model restriction:** This API can be used only in the stage model. |
## voiceButton<sup>23+</sup>

voiceButton(options: Optional\<VoiceButtonOptions\>)

Sets the voice button options. When enabled, a voice input button is displayed in the input box, allowing the user to enter text by voice.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 23.

**Parameters**

| Name| Type| Mandatory| Description|
| ----- | ----- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[VoiceButtonOptions](./ts-text-common-sys.md#voicebuttonoptions23)\> | Yes  | Voice button configuration options, used to control the enabled state and behavior of the voice input button. Use this parameter when the voice input feature needs to be enabled in the TextInput component. For details about the configuration items, see the VoiceButtonOptions type definition. |


## Examples

### Example 1: Setting a Voice Button

This example demonstrates how to enable the voice button for an input box by configuring the **voiceButton** API.

The [voiceButton](#voicebutton23) API is added since API version 23.

```ts
// xxx.ets
@Entry
@Component
struct TextInputExample {

  build() {
    Column() {
      TextInput().voiceButton({enabled: true})
    }
  }
}
```