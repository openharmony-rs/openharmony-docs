# Hid_EventProperties
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6bf705413e67f9d206cf9b81603cd89e87db21cc translatedAt=2026-11-04T03:42:27.306Z pushedAt=2026-11-04T10:12:49.977Z nl=1 -->

```c
typedef struct Hid_EventProperties {...} Hid_EventProperties
```

## Overview

Device event attributes, including the attribute encoding and value ranges of various event attributes such as event types, key values, absolute coordinates, and relative coordinates. Used for attribute configuration of HID devices, and applicable to scenarios that require fine-grained management of input events. Before using the struct, initialize all member variables according to the HID device specification.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| struct [Hid_EventTypeArray](capi-hidddk-hid-eventtypearray.md) hidEventTypes | Event type attribute encoding array, which contains the set of event types supported by the device and is used to configure the events that the HID device can trigger. |
| struct [Hid_KeyCodeArray](capi-hidddk-hid-keycodearray.md) hidKeys | Key code attribute encoding array, which contains the set of key codes supported by the device and is used to configure the key functions supported by the HID device. |
| struct [Hid_AbsAxesArray](capi-hidddk-hid-absaxesarray.md) hidAbs | Absolute coordinates attribute encoding array, which is used to configure absolute coordinate input (for example, touchscreens and joysticks). |
| struct [Hid_RelAxesArray](capi-hidddk-hid-relaxesarray.md) hidRelBits | Relative coordinates attribute encoding array, which is used to configure relative coordinate input (for example, mouse movement). |
| struct [Hid_MscEventArray](capi-hidddk-hid-msceventarray.md) hidMiscellaneous | Miscellaneous special event attribute encoding array, which is used to configure special input events (for example, scanning and gestures). |
| int32_t hidAbsMax[64] | Maximum value of the absolute coordinates attribute. Each array element corresponds to a coordinate axis by index and must be no less than the minimum value of the corresponding axis. |
| int32_t hidAbsMin[64] | Minimum value of the absolute coordinates attribute. Each array element corresponds to a coordinate axis by index and must be no greater than the maximum value of the corresponding axis. |
| int32_t hidAbsFuzz[64] | Fuzz value of the absolute coordinates attribute. Each array element corresponds to a coordinate axis by index and is used to define the fuzz tolerance of input events. It is recommended that this value not exceed the coordinate range. |
| int32_t hidAbsFlat[64] | Flat value of the absolute coordinates attribute. Each array element corresponds to a coordinate axis by index and is used to define the flat range of the input event dead zone (values within this range do not trigger event reporting). It is recommended that this value not exceed the fuzz value. |


