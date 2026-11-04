# Hid_RawDevInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T03:44:41.608Z pushedAt=2026-11-04T10:12:49.986Z nl=1 -->

```c
typedef struct Hid_RawDevInfo {...} Hid_RawDevInfo
```

## Overview

Describes the raw HID device information, including key identification information such as the bus type, vendor ID, and product ID. Developers can use this struct to identify and distinguish different HID devices, typically for device identification, device matching, and device filtering.

**Since**: 18

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t busType | Bus type, used to identify the physical connection mode of the HID device. |
| uint16_t vendor | Vendor ID. |
| uint16_t product | Product ID. |


