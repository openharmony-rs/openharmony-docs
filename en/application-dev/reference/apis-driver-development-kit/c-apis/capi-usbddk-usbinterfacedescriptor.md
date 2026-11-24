# UsbInterfaceDescriptor

```c
struct UsbInterfaceDescriptor {...}
```

## Overview

Defines standard interface descriptors, which correspond to **Standard Interface Descriptor** in the USB protocol.

<!--Device-struct UsbInterfaceDescriptor {...}--><!--Device-struct UsbInterfaceDescriptor {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t bLength | Size of this descriptor, in bytes.<br><!--Device-uint8_t bLength--><!--Device-uint8_t bLength-End--> |
| uint8_t bDescriptorType | Descriptor type.<br><!--Device-uint8_t bDescriptorType--><!--Device-uint8_t bDescriptorType-End--> |
| uint8_t bInterfaceNumber | Interface ID.<br><!--Device-uint8_t bInterfaceNumber--><!--Device-uint8_t bInterfaceNumber-End--> |
| uint8_t bAlternateSetting | Value used to select the alternate setting of the interface.<br><!--Device-uint8_t bAlternateSetting--><!--Device-uint8_t bAlternateSetting-End--> |
| uint8_t bNumEndpoints | Number of endpoints (excluding endpoint 0) used by the interface.<br><!--Device-uint8_t bNumEndpoints--><!--Device-uint8_t bNumEndpoints-End--> |
| uint8_t bInterfaceClass | Interface class code allocated by the USB-IF.<br><!--Device-uint8_t bInterfaceClass--><!--Device-uint8_t bInterfaceClass-End--> |
| uint8_t bInterfaceSubClass | Interface subclass code allocated by the USB-IF. The value is limited by that of **bInterfaceClass**.<br><!--Device-uint8_t bInterfaceSubClass--><!--Device-uint8_t bInterfaceSubClass-End--> |
| uint8_t bInterfaceProtocol | Interface protocol code allocated by the USB-IF. The value is limited by that of **bInterfaceClass** and **bInterfaceSubClass**.<br><!--Device-uint8_t bInterfaceProtocol--><!--Device-uint8_t bInterfaceProtocol-End--> |
| uint8_t iInterface | Index of the string descriptor that describes the interface.<br><!--Device-uint8_t iInterface--><!--Device-uint8_t iInterface-End--> |


