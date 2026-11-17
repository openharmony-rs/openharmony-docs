# Hid_KeyCodeArray

```c
typedef struct Hid_KeyCodeArray {...} Hid_KeyCodeArray
```

## Overview

Defines an array of key value attribute codes, which stores information about the key value codes supported by an HID device.

<!--Device-struct Hid_KeyCodeArray {...}--><!--Device-struct Hid_KeyCodeArray {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Hid_KeyCode](capi-hid-ddk-types-h.md#hid_keycode) *hidKeyCode | Pointer to the array of key codes, which points to the array pre-allocated by the caller. The pointer cannot be null. The array size must be greater than or equal to the value of length. |
| uint16_t length | Valid length of the array, which cannot exceed the actual length of the **hidKeyCode** array. |


