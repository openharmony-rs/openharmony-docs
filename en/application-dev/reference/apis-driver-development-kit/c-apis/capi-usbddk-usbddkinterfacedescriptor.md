# UsbDdkInterfaceDescriptor

```c
typedef struct UsbDdkInterfaceDescriptor {...} UsbDdkInterfaceDescriptor
```

## Overview

Defines USB interface descriptors.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct [UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) interfaceDescriptor | Standard USB interface descriptor. |
| struct [UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) *endPoint | Endpoint descriptor contained in the interface. |
| const uint8_t *extra | Unresolved descriptor, including class- or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor. |


