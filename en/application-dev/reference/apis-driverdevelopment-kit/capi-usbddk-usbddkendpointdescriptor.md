# UsbDdkEndpointDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:49:39.564Z pushedAt=2026-06-22T11:21:11.433Z -->

```c
typedef struct UsbDdkEndpointDescriptor {...} UsbDdkEndpointDescriptor
```

## Overview

Defines endpoint descriptors.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| struct UsbEndpointDescriptor endpointDescriptor | Standard endpoint descriptor.|
| const uint8_t* extra | Unresolved descriptor, including class- or vendor-specific descriptors.|
| uint32_t extraLength | Length of the unresolved descriptor.|