# UsbConfigDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:11:34.873Z pushedAt=2026-11-10T01:47:49.283Z nl=1 -->

```c
typedef struct UsbConfigDescriptor {...} __attribute__((packed)) UsbConfigDescriptor
```

## Overview

Defines standard configuration descriptors, which correspond to **Standard Configuration Descriptor** in the USB protocol.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t bLength | Size of this descriptor, in bytes. |
| uint8_t bDescriptorType | Descriptor type.|
| uint16_t wTotalLength | Total length of the configuration descriptor, including the configuration, interface, endpoint, and class- or vendor-specific descriptors, in bytes. |
| uint8_t bNumInterfaces | Number of interfaces supported by the configuration.|
| uint8_t bConfigurationValue | Value used to set the configuration and select the current configuration. |
| uint8_t iConfiguration | Index of the string descriptor that describes the configuration.|
| uint8_t bmAttributes | Configuration attributes, including the power supply mode and remote wakeup. |
| uint8_t bMaxPower | Maximum power consumption of the bus-powered USB device, in 2 mA.|


