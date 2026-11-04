# UsbDdkEndpointDescriptor
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T04:03:21.363Z pushedAt=2026-11-04T10:12:50.039Z nl=1 -->

```c
typedef struct UsbDdkEndpointDescriptor {...} UsbDdkEndpointDescriptor
```

## Overview

Describes an endpoint descriptor, including the standard endpoint descriptor and unparsed descriptor information.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [struct UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) endpointDescriptor | Standard endpoint descriptor.|
| const uint8_t* extra | Pointer to the unparsed descriptor, containing class-specific or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor.|


