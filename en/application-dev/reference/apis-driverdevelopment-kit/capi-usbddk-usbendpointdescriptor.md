# UsbEndpointDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-04T04:05:54.195Z pushedAt=2026-11-04T10:12:50.049Z nl=1 -->

```c
typedef struct UsbEndpointDescriptor {...} __attribute__((packed)) UsbEndpointDescriptor
```

## Overview

Defines standard endpoint descriptors, which correspond to **Standard Endpoint Descriptor** in the USB protocol.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t bLength | Size of this descriptor, in bytes. |
| uint8_t bDescriptorType | Descriptor type.|
| uint8_t bEndpointAddress | Endpoint address, including the endpoint number and endpoint direction.|
| uint8_t bmAttributes | Endpoint attributes, including the transfer type, synchronization type, and usage type. |
| uint16_t wMaxPacketSize | Maximum packet size supported by an endpoint, in bytes. |
| uint8_t bInterval | Interval for polling endpoints for data transfer. |
| uint8_t bRefresh | Refresh rate for audio devices.|
| uint8_t bSynchAddress | Endpoint synchronization address for audio devices.|


