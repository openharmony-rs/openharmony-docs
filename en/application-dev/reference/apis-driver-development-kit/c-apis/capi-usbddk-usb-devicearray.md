# Usb_DeviceArray

```c
typedef struct Usb_DeviceArray {...} Usb_DeviceArray
```

## Overview

Defines the device ID array, which is used to store the device IDs and device quantity obtained using [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). After using the structure, you must release the memory allocated for the device ID array. Otherwise, resource leaks may occur.

<!--Device-struct Usb_DeviceArray {...}--><!--Device-struct Usb_DeviceArray {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 18

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t* deviceIds | Pointer to the start address of the device ID array that you have applied for. To avoid excessive memory consumption, it is recommended that the maximum size of the allocated array be 128. |
| uint32_t num | Device quantity. Device IDs are obtained by traversing **deviceIds** based on the value of this parameter. If the value is **0**, there is no USB device. |


