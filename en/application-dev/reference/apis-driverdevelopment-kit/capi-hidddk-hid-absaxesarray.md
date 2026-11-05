# Hid_AbsAxesArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-04T03:40:24.972Z pushedAt=2026-11-04T10:12:49.970Z nl=1 -->

```c
typedef struct Hid_AbsAxesArray {...} Hid_AbsAxesArray
```

## Overview

An array of absolute coordinate attributes, used to store the attribute information of multiple absolute coordinate axes of an HID device. It supports describing the coordinate characteristics of input devices such as touchscreens and game joysticks, and is suitable for driver development scenarios that require precise reading and processing of multidimensional input data, for example, recording axis data in input devices such as gamepads and touchpads.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Hid_AbsAxes](capi-hid-ddk-types-h.md#hid_absaxes)* hidAbsAxes | Pointer to the first element of the array that encodes the absolute coordinate attributes. It must be used together with length, and the pointer must be valid and not NULL. |
| uint16_t length | Valid length of the array, indicating the number of valid elements pointed to by hidAbsAxes. Value range: [0, 65535]. |


