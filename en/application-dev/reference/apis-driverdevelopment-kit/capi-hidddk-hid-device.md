# Hid_Device
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_Device {...} Hid_Device
```

## Overview

Describes basic device information, including the name, vendor ID, and product ID of an HID device. This information is used as the device identifier when creating and operating an HID device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* deviceName | Device name, which can contain a maximum of 128 characters and cannot be null. If the length exceeds the upper limit or the value is null, an error is returned.|
| uint16_t vendorId | Vendor ID.|
| uint16_t productId | Product ID.|
| uint16_t version | Version.|
| uint16_t bustype | Bus type. For details about the value, see the bus type definition in the standard HID protocol.|
| Hid_DeviceProp* properties | Device properties. Before using this pointer, check whether it is null. This pointer is valid only when the **Hid_Device** object is valid and should not be manually released.|
| uint16_t propLength | Number of device properties, indicating the number of valid elements in the properties array. Note: When traversing the array, use this value as the boundary condition. The value may be **0**.|
