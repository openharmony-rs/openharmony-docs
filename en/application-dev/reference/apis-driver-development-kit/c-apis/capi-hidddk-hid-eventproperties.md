# Hid_EventProperties

```c
typedef struct Hid_EventProperties {...} Hid_EventProperties
```

## Overview

Defines a struct for the event properties of a device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| struct [Hid_EventTypeArray](capi-hidddk-hid-eventtypearray.md) hidEventTypes | Array of event types. |
| struct [Hid_KeyCodeArray](capi-hidddk-hid-keycodearray.md) hidKeys | Array of key codes. |
| struct [Hid_AbsAxesArray](capi-hidddk-hid-absaxesarray.md) hidAbs | Array of absolute coordinate properties. |
| struct [Hid_RelAxesArray](capi-hidddk-hid-relaxesarray.md) hidRelBits | Array of relative coordinate properties. |
| struct [Hid_MscEventArray](capi-hidddk-hid-msceventarray.md) hidMiscellaneous | Array of miscellaneous events. |
| int32_t hidAbsMax[64] | Maximum values of the absolute coordinates. |
| int32_t hidAbsMin[64] | Minimum values of the absolute coordinates. |
| int32_t hidAbsFuzz[64] | Fuzzy values of the absolute coordinates. |
| int32_t hidAbsFlat[64] | Fixed values of the absolute coordinates. |


