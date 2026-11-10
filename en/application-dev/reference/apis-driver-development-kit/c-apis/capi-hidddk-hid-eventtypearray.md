# Hid_EventTypeArray

```c
struct Hid_EventTypeArray {...}
```

## Overview

Defines an array of event type codes, which stores information about the event types supported by an HID device.

<!--Device-struct Hid_EventTypeArray {...}--><!--Device-struct Hid_EventTypeArray {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| Hid_EventType *hidEventType | Pointer to the array of event type codes, which points to the array pre-allocated by the caller. The pointer cannot be null. The array size must be greater than or equal to the value of length. |
| uint16_t length | Valid length of the array, which cannot exceed the actual length of the **hidEventType** array. |


