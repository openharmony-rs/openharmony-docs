# UsbDdkInterface

```c
typedef struct UsbDdkInterface {...} UsbDdkInterface
```

## Overview

Defines a USB DDK API, which is a collection of alternate settings for a particular USB interface.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t numAltsetting | Number of alternate settings of the USB interface. |
| struct [UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md) *altsetting | Alternate setting of the USB interface. |


