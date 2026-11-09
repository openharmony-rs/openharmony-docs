# UsbDdkInterface

```c
struct UsbDdkInterface {...}
```

## Overview

Defines a USB DDK API, which is a collection of alternate settings for a particular USB interface.

<!--Device-struct UsbDdkInterface {...}--><!--Device-struct UsbDdkInterface {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t numAltsetting | Number of alternate settings of the USB interface. |
| struct UsbDdkInterfaceDescriptor *altsetting | Pointer to the array of alternate settings of the USB interface. The length of the array is specified by **<br>numAltsetting**. |


