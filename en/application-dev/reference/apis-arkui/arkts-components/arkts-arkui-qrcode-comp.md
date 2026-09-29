# QRCode

The **QRCode** component is used to display a single QR code. It supports customizing the QR code color, background color, and content opacity, and is suitable for scenarios where a QR code needs to be displayed for scanning to obtain string information.

> **NOTE:** 
> 
> - This component is supported since API version 7. Newly added APIs in later versions are marked with a superscript to indicate their
> 
> - The pixel count of the **QRCode** component is related to its content. If the component size is too small, the content may not be displayed. In this case, adjust the component size appropriately. &gt;

## Child Components

Not supported

## QRCode

```TypeScript
QRCode(value: ResourceStr)
```

Creates a **QRCode** component. The displayed QR code can be scanned to obtain the encoded string information.

**Since:** 7

**Atomic service API:** This API can be used in atomic services since API version 11.

**Widget capability:** This API can be used in ArkTS widgets since API version 9.

<!--Device-QRCodeInterface-(value: ResourceStr): QRCodeAttribute--><!--Device-QRCodeInterface-(value: ResourceStr): QRCodeAttribute-End-->

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | QR code content string. It supports a maximum of 512 characters. If the limit is exceeded, only the first 512 characters are used.<br>Since API version 20, the Resource type is supported. <br>**Note:** <br>Setting it to null has the same effect as setting it to the string "null"; setting it to undefined has the same effect as setting it to the string "undefined"; passing an empty string generates an invalid QR code. |

## Summary

## Examples

### Example 1: Setting the Color, Background Color, and Opacity

This example demonstrates the basic usage of the QRCode component. It sets the QR code color using the [color](#color) attribute, the background color using the [backgroundColor](#backgroundcolor) attribute, and the opacity using the [contentOpacity](arkts-arkui-qrcode-comp-attribute.md#contentopacity) attribute.



```TypeScript
// xxx.ets
@Entry
@Component
struct QRCodeExample {
  private value: string = 'hello world';

  build() {
    Column({ space: 5 }) {
      Text('normal').width('90%').fontColor(0xCCCCCC).fontSize(30)
      QRCode(this.value).width(140).height(140)

      // Set the color of the QR code.
      Text('color').width('90%').fontColor(0xCCCCCC).fontSize(30)
      QRCode(this.value).color(0xF7CE00).width(140).height(140)

      // Set the background color of the QR code.
      Text('backgroundColor').width('90%').fontColor(0xCCCCCC).fontSize(30)
      QRCode(this.value).width(140).height(140).backgroundColor(Color.Orange)

      // Set the opacity of QR code content.
      Text('contentOpacity').width('90%').fontColor(0xCCCCCC).fontSize(30)
      QRCode(this.value).width(140).height(140).color(Color.Black).contentOpacity(0.1)
    }.width('100%').margin({ top: 5 })
  }
}
```

### Example 2: Setting the Background Color to Transparent

This example shows how to set the QR code background color to transparent using the [backgroundColor](#backgroundcolor) attribute, allowing the QR code content to blend with the background.

```TypeScript
// xxx.ets
@Entry
@Component
struct QRCodeExample {
  private value: string = 'hello world';

  build() {
    Column({ space: 5 }) {
      RelativeContainer() {
        // Replace $r('app.media.ocean') with the image resource file you use.
        Image($r('app.media.ocean'))
        // Set the QR code background color to transparent.
        QRCode(this.value).width(200).height(200).backgroundColor('#00ffffff')
      }.width(200).height(200)
    }.width('100%').margin({ top: 5 })
  }
}
```
