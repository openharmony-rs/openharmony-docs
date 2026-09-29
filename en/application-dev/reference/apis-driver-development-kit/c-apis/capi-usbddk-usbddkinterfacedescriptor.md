# UsbDdkInterfaceDescriptor

```c
struct UsbDdkInterfaceDescriptor {...}
```

## Overview

Defines USB interface descriptors.

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) interfaceDescriptor | Standard USB interface descriptor. |
| struct UsbDdkEndpointDescriptor *endPoint | Endpoint descriptor contained in the interface. |
| const uint8_t *extra | Unresolved descriptor, including class- or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor. |


