# UsbDdkConfigDescriptor

```c
struct UsbDdkConfigDescriptor {...}
```

## Overview

Defines configuration descriptors.

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct UsbConfigDescriptor](capi-usbddk-usbconfigdescriptor.md) configDescriptor | Standard configuration descriptor. |
| struct UsbDdkInterface *interface | Interfaces contained in the configuration. |
| const uint8_t *extra | Unresolved descriptor, including class- or vendor-specific descriptors. |
| uint32_t extraLength | Length of the unresolved descriptor. |


