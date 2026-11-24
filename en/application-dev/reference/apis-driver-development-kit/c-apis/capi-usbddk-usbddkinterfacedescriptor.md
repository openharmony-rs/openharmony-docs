# UsbDdkInterfaceDescriptor

```c
typedef struct UsbDdkInterfaceDescriptor {...} UsbDdkInterfaceDescriptor
```

## Overview

Defines interface descriptors, including standard interface descriptors and endpoint descriptors.

<!--Device-struct UsbDdkInterfaceDescriptor {...}--><!--Device-struct UsbDdkInterfaceDescriptor {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct UsbInterfaceDescriptor](capi-usbddk-usbinterfacedescriptor.md) interfaceDescriptor | Standard USB interface descriptor.<br><!--Device-struct UsbInterfaceDescriptor interfaceDescriptor--><!--Device-struct UsbInterfaceDescriptor interfaceDescriptor-End--> |
| [struct UsbDdkEndpointDescriptor](capi-usbddk-usbddkendpointdescriptor.md) *endPoint | Endpoint descriptor contained in the interface. This parameter can be a null pointer, indicating that there is no endpoint (excluding control endpoint 0).<br><!--Device-struct UsbDdkEndpointDescriptor *endPoint--><!--Device-struct UsbDdkEndpointDescriptor *endPoint-End--> |
| const uint8_t *extra | Pointer to the unresolved descriptor, including class- or vendor-specific descriptors.<br><!--Device-const uint8_t *extra--><!--Device-const uint8_t *extra-End--> |
| uint32_t extraLength | Length of the unresolved descriptor.<br><!--Device-uint32_t extraLength--><!--Device-uint32_t extraLength-End--> |


