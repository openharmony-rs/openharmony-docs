# UsbDdkEndpointDescriptor

```c
typedef struct UsbDdkEndpointDescriptor {...} UsbDdkEndpointDescriptor
```

## Overview

Defines endpoint descriptors.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct [UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) endpointDescriptor | Standard endpoint descriptor. |
| const uint8_t *extra | Unresolved descriptor, including class- or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor. |


