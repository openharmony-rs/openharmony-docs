# Hid_AbsAxesArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_AbsAxesArray {...} Hid_AbsAxesArray
```

## Overview

Defines an array of absolute coordinate attributes, which stores attributes about multiple absolute coordinate axes of an HID device. These attributes can be used to describe coordinate features of input devices such as touchscreens and game analog sticks. This struct is applicable to driver development scenarios that require precise reading and processing of multi-dimensional input data, for example, recording axis position data in input devices such as game controllers and touchpads.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Hid_AbsAxes](capi-hid-ddk-types-h.md#hid_absaxes)* hidAbsAxes | Pointer to the first element of the array of absolute coordinate codes. This parameter must be used together with **length**. The pointer must be valid and cannot be null.|
| uint16_t length | Valid length of the array, indicating the number of valid elements to which the **hidAbsAxes** pointer points. The value range is [0, 65535].|
