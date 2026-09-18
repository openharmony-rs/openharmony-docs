# PasteButton

**PasteButton** is a security component that provides paste functionality. When users tap this component, the application temporarily gains pasteboard read permissions. <br>**Description**</br>

## Key Enums

&lt;li&gt;[PasteIconStyle](arkts-arkui-pasteiconstyle-e.md): Enumeration of icon styles for the paste button. Specifies the icon style displayed.&lt;/li&gt; &lt;li&gt;[PasteDescription](arkts-arkui-pastedescription-e.md): Enumeration of text descriptions for the paste button. Specifies the text description displayed.&lt;/li&gt; &lt;li&gt;[PasteButtonOnClickResult](arkts-arkui-pastebuttononclickresult-e.md): Enumeration of click results for the paste button. Indicates whether authorization succeeds after a click.&lt;/li&gt;

## Key APIs

&lt;li&gt;[PasteButtonOptions](arkts-arkui-pastebuttonoptions-i.md): Configuration object for the paste button. Defines properties including icon, text and button type.&lt;/li&gt; &lt;li&gt;[PasteButtonCallback](arkts-arkui-pastebuttoncallback-t.md): Callback for paste button clicks. Returns click events, authorization results and error messages.&lt;/li&gt;

## Child Components

&lt;li&gt;Not supported.&lt;/li&gt;&lt;/ul&gt;

## PasteButton

```TypeScript
PasteButton()
```

Creates a **PasteButton** component with an icon, text, and background by default. After creation, the system triggers an authorization check when the button is tapped. Upon successful authorization, the application gains permission to read the current clipboard content. <br>**Description**&lt;/br&gt; &lt;ul&gt;&lt;li&gt;You may want to learn the [restrictions on security component styles](../../../security/AccessToken/security-component-overview.md#constraints) to avoid authorization failures caused by incompliant styles.&lt;/li&gt;&lt;/ul&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

## PasteButton

```TypeScript
PasteButton(options: PasteButtonOptions)
```

Creates a paste button with the specified icon, text and button type. After creation, the system triggers an authorization check when the button is tapped. Upon successful authorization, the app gains temporary permission to read the clipboard. <br>**Description**&lt;/br&gt; &lt;ul&gt;&lt;li&gt;You may want to learn the [restrictions on security component styles](../../../security/AccessToken/security-component-overview.md#constraints) to avoid authorization failures caused by incompliant styles.&lt;/li&gt;&lt;/ul&gt;

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [PasteButtonOptions](arkts-arkui-pastebuttonoptions-i.md) | Yes | Configuration options for the paste button, used to set properties such as icon, text and button type.<br>You are advised to explicitly set at least one of **icon** or **text** to help users identify the button. <br>If neither **icon** nor **text** is specified, **options** does not take effect and the button is displayed in the default style.<br>{<br>icon: PasteIconStyle.LINES,<br>text:PasteDescription.PASTE, <br>buttonType: ButtonType.Capsule <br>}. |

## Summary

### Interfaces

| Name | Description |
| --- | --- |
| [PasteButtonOptions](arkts-arkui-pastebuttonoptions-i.md) | Defines options for the paste button, including icon, text and button type. |

### Types

| Name | Description |
| --- | --- |
| [PasteButtonCallback](arkts-arkui-pastebuttoncallback-t.md) | Triggered when the **PasteButton** component is clicked. |

### Enums

| Name | Description |
| --- | --- |
| [PasteButtonOnClickResult](arkts-arkui-pastebuttononclickresult-e.md) | Enumerates the authorization results after the **PasteButton** component is tapped. |
| [PasteDescription](arkts-arkui-pastedescription-e.md) | Enumerates the text that can be displayed on the paste button. |
| [PasteIconStyle](arkts-arkui-pasteiconstyle-e.md) | Enumerates icon styles of the **PasteButton** component. |

## Examples

```TypeScript
// xxx.ets
import { BusinessError } from '@kit.BasicServicesKit';

@Entry
@Component
struct Index {
  // Define the callback for processing the authorization result and error information when the paste button is clicked.
  handlePasteButtonClick: PasteButtonCallback =
    (event: ClickEvent, result: PasteButtonOnClickResult, error?: BusinessError<void>) => {
      if (result === PasteButtonOnClickResult.SUCCESS) {
        console.info('success');
      } else {
        console.error('errCode: ' + error?.code);
        console.error('errMessage: ' + error?.message);
      }
    };

  build() {
    Row() {
      Column({ space: 10 }) {
        // Create a default PasteButton component with an icon, text, and background.
        PasteButton().onClick(this.handlePasteButtonClick)
        // Whether an element is contained depends on whether the parameter corresponding to the element is specified. If buttonType is not passed in, the button uses the ButtonType.Capsule settings.
        PasteButton({ icon: PasteIconStyle.LINES })
        // Create a button with only an icon and background. If the alpha value of the most significant eight bits of the background color is less than 0x1a, the system forcibly adjusts the alpha value to 0xff.
        PasteButton({ icon: PasteIconStyle.LINES, buttonType: ButtonType.Capsule })
          .backgroundColor(0x10007dff)
        // Create a button with an icon, text, and background. If the alpha value of the most significant eight bits of the background color is less than 0x1a, the system forcibly adjusts the alpha value to 0xff.
        PasteButton({ icon: PasteIconStyle.LINES, text: PasteDescription.PASTE, buttonType: ButtonType.Capsule })
        // Create a button with an icon, text, and background. If the set width is less than the minimum allowed, the button's text will wrap to guarantee full text display.
        PasteButton({ icon: PasteIconStyle.LINES, text: PasteDescription.PASTE, buttonType: ButtonType.Capsule })
          .fontSize(16)
          .width(30)
        // Create a button with an icon, text, and background. If the set width is less than the minimum allowed, the button's text will wrap to guarantee full text display.
        PasteButton({ icon: PasteIconStyle.LINES, text: PasteDescription.PASTE, buttonType: ButtonType.Capsule })
          .fontSize(16)
          .size({ width: 30, height: 30 })
        // Create a button with an icon, text, and background. If the set width is less than the minimum allowed, the button's text will wrap to guarantee full text display.
        PasteButton({ icon: PasteIconStyle.LINES, text: PasteDescription.PASTE, buttonType: ButtonType.Capsule })
          .fontSize(16)
          .constraintSize({
            minWidth: 0,
            maxWidth: 30,
            minHeight: 0,
            maxHeight: 30
          })
      }.width('100%')
    }.height('100%')
  }
}
```
