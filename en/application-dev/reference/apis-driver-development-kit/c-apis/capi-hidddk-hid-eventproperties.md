# Hid_EventProperties

```c
typedef struct Hid_EventProperties {...} Hid_EventProperties
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
| [struct Hid_EventTypeArray](capi-hidddk-hid-eventtypearray.md) hidEventTypes | Array of event types, which contains the set of event types supported by the device. This parameter is used to configure the events that can be triggered by the HID device.<br><!--Device-struct Hid_EventTypeArray hidEventTypes--><!--Device-struct Hid_EventTypeArray hidEventTypes-End--> |
| [struct Hid_KeyCodeArray](capi-hidddk-hid-keycodearray.md) hidKeys | Array of key codes, which contains the set of key codes supported by the device. This parameter is used to configure the key functions supported by the HID device.<br><!--Device-struct Hid_KeyCodeArray hidKeys--><!--Device-struct Hid_KeyCodeArray hidKeys-End--> |
| [struct Hid_AbsAxesArray](capi-hidddk-hid-absaxesarray.md) hidAbs | Array of absolute coordinate codes, which is used to configure absolute coordinate input (such as touchscreen and analog stick).<br><!--Device-struct Hid_AbsAxesArray hidAbs--><!--Device-struct Hid_AbsAxesArray hidAbs-End--> |
| [struct Hid_RelAxesArray](capi-hidddk-hid-relaxesarray.md) hidRelBits | Array of relative coordinate codes, which is used to configure relative coordinate input (such as mouse movement).<br><!--Device-struct Hid_RelAxesArray hidRelBits--><!--Device-struct Hid_RelAxesArray hidRelBits-End--> |
| [struct Hid_MscEventArray](capi-hidddk-hid-msceventarray.md) hidMiscellaneous | Array of miscellaneous events, which is used to configure miscellaneous input events (such as scanning and gestures).<br><!--Device-struct Hid_MscEventArray hidMiscellaneous--><!--Device-struct Hid_MscEventArray hidMiscellaneous-End--> |
| int32_t hidAbsMax[64] | Maximum values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and must be greater than or equal to the minimum value of the corresponding coordinate axis.<br><!--Device-int32_t hidAbsMax[64]--><!--Device-int32_t hidAbsMax[64]-End--> |
| int32_t hidAbsMin[64] | Minimum values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and must be less than or equal to the maximum value of the corresponding coordinate axis.<br><!--Device-int32_t hidAbsMin[64]--><!--Device-int32_t hidAbsMin[64]-End--> |
| int32_t hidAbsFuzz[64] | Fuzzy values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and are used to define the fuzzy tolerance of the input event. It is recommended that the value be less than or equal to the coordinate range.<br><!--Device-int32_t hidAbsFuzz[64]--><!--Device-int32_t hidAbsFuzz[64]-End--> |
| int32_t hidAbsFlat[64] | Flat values of the absolute coordinates. Elements in the array correspond to each coordinate axis by index and are used to define the flat range of the dead zone of the input event (values within this range do not trigger event reporting). It is recommended that the value be less than or equal to the fuzzy value.<br><!--Device-int32_t hidAbsFlat[64]--><!--Device-int32_t hidAbsFlat[64]-End--> |


