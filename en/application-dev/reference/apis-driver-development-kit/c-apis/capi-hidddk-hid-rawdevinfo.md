# Hid_RawDevInfo

```c
typedef struct Hid_RawDevInfo {...} Hid_RawDevInfo
```

## Overview

Describes the original HID device information, including key identifiers such as the bus type, vendor ID, and product ID. You can use this struct to identify and distinguish different HID devices. It is typically used in scenarios such as device identification, device matching, and device filtering.

<!--Device-struct Hid_RawDevInfo {...}--><!--Device-struct Hid_RawDevInfo {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 18

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t busType | Bus type, which identifies the physical connection method of the HID device.<br><!--Device-uint32_t busType--><!--Device-uint32_t busType-End--> |
| uint16_t vendor | Vendor ID.<br><!--Device-uint16_t vendor--><!--Device-uint16_t vendor-End--> |
| uint16_t product | Product ID.<br><!--Device-uint16_t product--><!--Device-uint16_t product-End--> |


