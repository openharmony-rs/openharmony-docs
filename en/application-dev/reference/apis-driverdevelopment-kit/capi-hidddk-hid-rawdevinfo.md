# Hid_RawDevInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_RawDevInfo {...} Hid_RawDevInfo
```

## Overview

Describes the original HID device information, including key identifiers such as the bus type, vendor ID, and product ID. You can use this struct to identify and distinguish different HID devices. It is typically used in scenarios such as device identification, device matching, and device filtering.

**Since**: 18

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t busType | Bus type, which identifies the physical connection method of the HID device.|
| uint16_t vendor | Vendor ID.|
| uint16_t product | Product ID.|
