# QRCode

The **QRCode** component is used to display a QR code.

> **NOTE** > > - The pixel count of the **QRCode** component is subject to the content. If the component size is not large enough, > the content may fail to be displayed. In this case, you need to resize the component.

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

**System capability:** SystemCapability.ArkUI.ArkUI.Full

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | [ResourceStr](../arkts-apis/arkts-arkui-resourcestr-t.md) | Yes | Content of the QR code. A maximum of 512 characters are supported. If this limit is exceeded, the first 512 characters are used.<br>The Resource type is supported since API version 20.<br> **NOTE:** <br>If this parameter is set to **null**, it is equivalent to passing the string **"null"**. If it is set to **undefined**, it is equivalent to passing the string **"undefined"**. Passing an empty string will result in an invalid QR code. |

## Summary

## Examples

```TypeScript
### Example 1: Setting the Color, Background Color, and Opacity

This example demonstrates the basic usage of the QRCode component. It sets the QR code color using the [color](#color) attribute, the background color using the [backgroundColor](#backgroundcolor) attribute, and the opacity using the [contentOpacity](arkts-arkui-qrcode-comp-attribute.md#contentopacity) attribute.


```

```TypeScript
### Example 2: Setting the Background Color to Transparent

This example shows how to set the QR code background color to transparent using the [backgroundColor](#backgroundcolor) attribute, allowing the QR code content to blend with the background.
```
