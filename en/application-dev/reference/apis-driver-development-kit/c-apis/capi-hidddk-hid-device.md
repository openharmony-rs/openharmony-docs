# Hid_Device

```c
typedef struct Hid_Device {...} Hid_Device
```

## Overview

Defines a struct for basic device information.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const char *deviceName | Device name. |
| uint16_t vendorId | Vendor ID. |
| uint16_t productId | Product ID. |
| uint16_t version | Version number. |
| uint16_t bustype | Bus type. |
| [Hid_DeviceProp](capi-hid-ddk-types-h.md#hid_deviceprop) *properties | Device properties indicated by [Hid_DeviceProp](capi-hid-ddk-types-h.md#hid_deviceprop). |
| uint16_t propLength | Number of device properties. |


