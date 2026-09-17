# FormLink

The **FormLink** component is provided for interactions between static widgets and widget providers. It supports three types of events: router, message, and call.

> **NOTE** > > - This component is supported since API version 10. Updates will be marked with a superscript to indicate their > earliest API version. > > - This component can be used only in static widgets. > > - This document covers static widget development only. For comprehensive widget development guidance, see the > [widget development guide](../../../form/formkit-overview.md).

## FormLink

```TypeScript
FormLink(options: FormLinkOptions)
```

Init FormLink component with options.

**Since:** 10

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 10.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [FormLinkOptions](arkts-arkui-formlinkoptions-i.md) | Yes | Widget information. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [FormLinkOptions](arkts-arkui-formlinkoptions-i.md) | Defines the FormLink options. |

## Examples

```TypeScript
@Entry
@Component
struct FormLinkDemo {
  build() {
    Column() {
      Text("This is a static widget").fontSize(20).margin(10)

      // The router event is used to redirect to the specified UIAbility from the static widget.
      FormLink({
        action: "router",
        abilityName: "EntryAbility",
        params: {
          'message': 'testForRouter' // Customize the message to send.
        }
      }) {
        Button("router event").width(120)
      }.margin(10)


      // The message event triggers the onFormEvent callback of FormExtensionAbility.
      FormLink({
        action: "message",
        abilityName: "EntryAbility",
        params: {
          'message': 'messageEvent' // Customize the message to send.
        }
      }) {
        Button("message event").width(120)
      }.margin(10)


      // The call event is used to call the specified method in the UIAbility.
      FormLink({
        action: "call",
        abilityName: "EntryAbility",
        params: {
          'method': 'funA', // Set the name of the method to call in the EntryAbility.
          'num': 1 // Set other parameters to be passed in.
        }
      }) {
        Button("call event").width(120)
      }.margin(10)

      // The router event is used to redirect to the specified UIAbility from the static widget through deep linking.
      FormLink({
        action: "router",
        uri: 'example://uri.ohos.com/link_page',
        params: {
          message:'router msg for static uri deeplink' // Customize the message to send.
        }
      }) {
        Button("deeplink event").width(120)
      }.margin(10)
    }
    .justifyContent(FlexAlign.Center)
    .width('100%').height('100%')
  }
}
```

```TypeScript


The following is an example of uris configuration in the [module.json5](../../../quick-start/module-configuration-file.md#skills) file of the target application:
```
