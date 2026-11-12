# UsbDdkConfigDescriptor

```c
typedef struct UsbDdkConfigDescriptor {...} UsbDdkConfigDescriptor
```

## Overview

Defines configuration descriptors, including standard configuration descriptors and interface descriptors.

<!--Device-struct UsbDdkConfigDescriptor {...}--><!--Device-struct UsbDdkConfigDescriptor {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) configDescriptor | Standard configuration descriptor. |
| [struct UsbDdkInterface](capi-usbddk-usbddkinterface.md) *interface | Interfaces contained in the configuration. |
| const uint8_t *extra | Pointer to the unresolved descriptor, including class- or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor. |


