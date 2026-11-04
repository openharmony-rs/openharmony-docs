# UsbDdkInterface
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T04:03:20.538Z pushedAt=2026-11-04T10:12:50.036Z nl=1 -->

```c
typedef struct UsbDdkInterface {...} UsbDdkInterface
```

## Overview

Defines a USB DDK API, which is a collection of alternate settings for a particular USB interface.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t numAltsetting | Number of alternate settings of the USB interface. |
| [struct UsbDdkInterfaceDescriptor](capi-usbddk-usbddkinterfacedescriptor.md)* altsetting | Pointer to the array of alternate settings of the USB interface. The length of the array is specified by **numAltsetting**. |


