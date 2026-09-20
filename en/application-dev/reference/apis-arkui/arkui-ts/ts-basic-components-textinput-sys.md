# TextInput (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-09-03T12:41:29.196Z pushedAt=2026-09-17T01:45:01.686Z -->

The **TextInput** component provides single-line text input, which is used to receive a single-line text input from a user. It supports multiple input types, such as password and voice, and can be used in scenarios such as form filling, search boxes, and login and registration, helping you quickly build user interaction interfaces.

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
| SCREEN_LOCK_PASSWORD<sup>11+</sup> | 9 | Lock screen password input mode. This mode accepts digits, letters, underscores (_), spaces, and special characters. An eye icon is used to show or hide the password, and the entered text is hidden behind dots by default. Since API version 12, on wearable, the entered text is displayed directly as dots. The password input mode does not support underlines. <br>**System API:** This is a system API.<br>**Model restriction:** This API can be used only in the stage model. |
## voiceButton<sup>23+</sup>

voiceButton(options: Optional\<VoiceButtonOptions\>)

Sets the voice button options. When enabled, a voice input button is displayed in the text box, allowing the user to enter text by voice.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 23.

**Parameters**

| Name| Type| Mandatory| Description|
| ----- | ----- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt)\<[VoiceButtonOptions](./ts-text-common-sys.md#voicebuttonoptions23)\> | Yes  | Voice button options, used to control the enabled state and behavior of the voice input button. Use this parameter when the voice input feature needs to be enabled in the **TextInput** component. For details about the configuration items, see the **VoiceButtonOptions** type definition. |


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