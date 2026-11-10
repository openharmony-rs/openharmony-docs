# Hid_EventProperties

```c
struct Hid_EventProperties {...}
```

## Overview

Defines device event attributes, including the event type, key value, absolute coordinate, and relative coordinate, as well as their attribute codes and value ranges. Defines the property configuration of an HID device. This struct is applicable to scenarios that require refined management of input events. Before using this struct, initialize all member variables based on the HID device specifications.

<!--Device-struct Hid_EventProperties {...}--><!--Device-struct Hid_EventProperties {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [struct Hid_EventTypeArray](capi-hidddk-hid-eventtypearray.md) hidEventTypes | Pointer to the array of event type codes, which points to the array pre-allocated by the caller. The pointer cannot be null. The array size must be greater than or equal to the value of length. |
| [struct Hid_KeyCodeArray](capi-hidddk-hid-keycodearray.md) hidKeys | Array of key codes, which contains the set of key codes supported by the device. This parameter is used to configure the key functions supported by the HID device. |
| [struct Hid_AbsAxesArray](capi-hidddk-hid-absaxesarray.md) hidAbs | Array of absolute coordinate codes, which is used to configure absolute coordinate input (such as touchscreen and analog stick). |
| [struct Hid_RelAxesArray](capi-hidddk-hid-relaxesarray.md) hidRelBits | Array of relative coordinate codes, which is used to configure relative coordinate input (such as mouse movement). |
| [struct Hid_MscEventArray](capi-hidddk-hid-msceventarray.md) hidMiscellaneous | Array of miscellaneous events, which is used to configure miscellaneous input events (such as scanning and gestures). |
| int32_t hidAbsMax | Maximum values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and must be greater than or equal to the minimum value of the corresponding coordinate axis. |
| int32_t hidAbsMin | Minimum values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and must be less than or equal to the maximum value of the corresponding coordinate axis. |
| int32_t hidAbsFuzz | Fuzzy values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and are used to define the fuzzy tolerance of the input event. It is recommended that the value be less than or equal to the coordinate range. |
| int32_t hidAbsFlat | Flat values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and are used to define the flat range of the dead zone of the input event (values within this range do not trigger event reporting). It is recommended that the value be less than or equal to the fuzzy value. |


