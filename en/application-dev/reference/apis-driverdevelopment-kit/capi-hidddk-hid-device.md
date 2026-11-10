# Hid_Device
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:08:34.285Z pushedAt=2026-11-10T01:38:57.500Z nl=1 -->

```c
typedef struct Hid_Device {...} Hid_Device
```

## Overview

Basic device information, used to represent the basic attributes of an HID device, such as its name, vendor ID, and product ID. It is used as a device identifier when creating and operating an HID device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| const char* deviceName | Pointer to the device name. The maximum length is 128 characters, and the value cannot be NULL. An error is returned if the length is exceeded or the value is NULL. |
| uint16_t vendorId | Vendor ID. |
| uint16_t productId | Product ID. |
| uint16_t version | Version number. |
| uint16_t bustype | Bus type. For the value meanings, refer to the bus type definitions in the standard HID protocol. |
| Hid_DeviceProp* properties | Device properties. Check whether the pointer is null before use. This pointer is valid only while the Hid_Device object is valid and must not be released manually. |
| uint16_t propLength | Number of device properties, indicating the number of valid elements in the properties array. Note: Use this value as the boundary condition when traversing the array. This value may be 0. |


