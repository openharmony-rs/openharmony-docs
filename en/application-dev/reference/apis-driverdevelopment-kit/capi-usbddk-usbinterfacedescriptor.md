# UsbInterfaceDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:49:57.582Z pushedAt=2026-06-22T11:21:11.443Z -->

```c
typedef struct UsbInterfaceDescriptor {...} __attribute__((packed)) UsbInterfaceDescriptor
```

## Overview

Defines standard interface descriptors, which correspond to **Standard Interface Descriptor** in the USB protocol.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t bLength | Size of the descriptor, in bytes.|
| uint8_t bDescriptorType | Descriptor type.|
| uint8_t bInterfaceNumber | Interface ID.|
| uint8_t bAlternateSetting | Value used to select the alternate setting of the interface.|
| uint8_t bNumEndpoints | Number of endpoints (excluding endpoint 0) used by the interface.|
| uint8_t bInterfaceClass | Interface class code allocated by the USB-IF.|
| uint8_t bInterfaceSubClass | Interface subclass code allocated by the USB-IF. The value is limited by that of **bInterfaceClass**.|
| uint8_t bInterfaceProtocol | Interface protocol code allocated by the USB-IF. The value is limited by that of **bInterfaceClass** and **bInterfaceSubClass**.|
| uint8_t iInterface | Index of the string descriptor that describes the interface.|