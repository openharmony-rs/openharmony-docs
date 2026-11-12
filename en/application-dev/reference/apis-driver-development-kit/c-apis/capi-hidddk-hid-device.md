# Hid_Device

```c
typedef struct Hid_Device {...} Hid_Device
```

## Overview

Describes basic device information, including the name, vendor ID, and product ID of an HID device. This information is used as the device identifier when creating and operating an HID device.

<!--Device-struct Hid_Device {...}--><!--Device-struct Hid_Device {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *deviceName | Device name, which can contain a maximum of 128 characters and cannot be null. If the length exceeds the upper limit or the value is null, an error is returned. |
| uint16_t vendorId | Vendor ID. |
| uint16_t productId | Product ID. |
| uint16_t version | Version. |
| uint16_t bustype | Bus type. For details about the value, see the bus type definition in the standard HID protocol. |
| [Hid_DeviceProp](capi-hid-ddk-types-h.md#hid_deviceprop) *properties | Device properties. Before using this pointer, check whether it is null. This pointer is valid only when the **Hid_Device** object is valid and should not be manually released. |
| uint16_t propLength | Number of device properties, indicating the number of valid elements in the properties array. Note: When traversing the array, use this value as the boundary condition. The value may be **0**. |


