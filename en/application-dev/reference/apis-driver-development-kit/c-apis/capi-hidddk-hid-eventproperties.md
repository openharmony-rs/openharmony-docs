# Hid_EventProperties

```c
struct Hid_EventProperties {...}
```

## Overview

Defines a struct for the event properties of a device.

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct Hid_EventTypeArray hidEventTypes | Array of event types. |
| struct Hid_KeyCodeArray hidKeys | Array of key codes. |
| struct Hid_AbsAxesArray hidAbs | Array of absolute coordinate properties. |
| struct Hid_RelAxesArray hidRelBits | Array of relative coordinate properties. |
| struct Hid_MscEventArray hidMiscellaneous | Array of miscellaneous events. |
| int32_t hidAbsMax | Maximum values of the absolute coordinates. |
| int32_t hidAbsMin | Minimum values of the absolute coordinates. |
| int32_t hidAbsFuzz | Fuzzy values of the absolute coordinates. |
| int32_t hidAbsFlat | Fixed values of the absolute coordinates. |


