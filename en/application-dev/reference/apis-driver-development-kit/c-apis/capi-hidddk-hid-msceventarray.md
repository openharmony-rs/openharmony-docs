# Hid_MscEventArray

```c
typedef struct Hid_MscEventArray {...} Hid_MscEventArray
```

## Overview

Defines an array of miscellaneous events, which stores information about the miscellaneous events supported by an HID device.

<!--Device-struct Hid_MscEventArray {...}--><!--Device-struct Hid_MscEventArray {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Hid_MscEvent](capi-hid-ddk-types-h.md#hid_mscevent) *hidMscEvent | Pointer to the array of miscellaneous events, which points to the array pre-allocated by the caller. The pointer cannot be null. The array size must be greater than or equal to the value of length. |
| uint16_t length | Valid length of the array, which cannot exceed the actual length of the **hidEventType** array. |


