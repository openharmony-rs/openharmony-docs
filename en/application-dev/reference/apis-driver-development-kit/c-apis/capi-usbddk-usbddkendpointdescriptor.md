# UsbDdkEndpointDescriptor

```c
typedef struct UsbDdkEndpointDescriptor {...} UsbDdkEndpointDescriptor
```

## Overview

Defines endpoint descriptors, including standard endpoint descriptors and descriptors that are not parsed.

<!--Device-struct UsbDdkEndpointDescriptor {...}--><!--Device-struct UsbDdkEndpointDescriptor {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct UsbEndpointDescriptor](capi-usbddk-usbendpointdescriptor.md) endpointDescriptor | Standard endpoint descriptor. |
| const uint8_t *extra | Pointer to the unresolved descriptor, including class- or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor. |


