# TextArea (System API)
<!--Kit: ArkUI-->
<!--Subsystem: ArkUI-->
<!--Owner: @kangshihui-->
<!--Designer: @xiangyuan6-->
<!--Tester: @jiaoaozihao-->
<!--Adviser: @Brilliantry_Rui-->

The **TextArea** component supports multi-line text input.

> **NOTE**
>
> - This component is supported since API version 7. Updates will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only system APIs provided by the module. For details about its public APIs, see [TextArea](ts-basic-components-textarea.md).

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

<!--no_check-->