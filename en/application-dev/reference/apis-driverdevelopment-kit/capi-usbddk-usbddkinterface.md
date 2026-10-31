# UsbDdkInterface
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=7a90ca54c554d40c3a0e04bd451a1fa4f12897ef translatedAt=2026-10-14T04:59:05.149Z pushedAt=2026-10-22T04:35:24.857Z nl=2 -->

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


