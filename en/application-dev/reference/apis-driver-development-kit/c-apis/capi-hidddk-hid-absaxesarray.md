# Hid_AbsAxesArray

```c
typedef struct Hid_AbsAxesArray {...} Hid_AbsAxesArray
```

## Overview

Defines an array of absolute coordinate attributes, which stores attributes about multiple absolute coordinate axes of an HID device. These attributes can be used to describe coordinate features of input devices such as touchscreens and game analog sticks. This struct is applicable to driver development scenarios that require precise reading and processing of multi-dimensional input data, for example, recording axis position data in input devices such as game controllers and touchpads.

<!--Device-struct Hid_AbsAxesArray {...}--><!--Device-struct Hid_AbsAxesArray {...}-End-->

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

**Related module**: [HidDdk](capi-driver-development-kit-hidddk.md)

**Header file**: [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [Hid_AbsAxes](capi-hid-ddk-types-h.md#hid_absaxes) *hidAbsAxes | Pointer to the first element of the array of absolute coordinate codes. This parameter must be used together with **length**. The pointer must be valid and cannot be null. |
| uint16_t length | Valid length of the array, which cannot exceed the actual length of the **hidEventType** array. |


