# TextArea (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @jiaxiaguang-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->
<!-- md-trans-meta sourceCommit=89682c631d1be2b78acdb9477c9eda01133e0baf translatedAt=2026-09-03T12:30:43.709Z -->

A multi-line text input component that supports extending input capabilities through system APIs such as the voice button. It is suitable for scenarios where users need to enter multiple lines of text, such as comment section messages, form filling, and note editing, improving input efficiency and reducing manual input costs.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This page contains only the system APIs of this module. For details about other public APIs, see [TextArea](ts-basic-components-textarea.md).

## voiceButton<sup>23+</sup>

voiceButton(options: Optional\<VoiceButtonOptions\>)

Sets the voice button options.

**System API**: This is a system API.

**Model restriction**: This API can be used only in the stage model.

**System capability**: SystemCapability.ArkUI.ArkUI.Full

**Atomic service API**: This API can be used in atomic services since API version 23.

**Parameters**

| Name| Type| Mandatory| Description|
| ----- | ----- | ---- | ---- |
| options | [Optional](ts-universal-attributes-custom-property.md#optionalt)<[VoiceButtonOptions](./ts-text-common-sys.md#voicebuttonoptions23)> | Yes | Voice Button options, used to configure the voice input button function of the input box. This parameter is of the Optional type. If no specific option value is specified, the system default Voice Button configuration is used. |


## Examples

### Example 1: Setting a Voice Button

This example demonstrates how to enable the voice input button for an input box by configuring the **voiceButton** API.

The [voiceButton](#voicebutton23) API is added since API version 23.

```ts
// xxx.ets
@Entry
@Component
struct TextAreaExample {

  build() {
    Column() {
      TextArea().voiceButton({enabled: true})
    }
  }
}
```