# Hid_RelAxesArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:09:16.641Z pushedAt=2026-11-10T01:40:11.928Z nl=1 -->

```c
typedef struct Hid_RelAxesArray {...} Hid_RelAxesArray
```

## Overview

Relative axis attribute encoding array, used to store the relative axis attribute information supported by the HID device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Hid_RelAxes](capi-hid-ddk-types-h.md#hid_relaxes)* hidRelAxes | Pointer to the array of relative coordinate attribute codes, which points to the array pre-allocated by the caller (must not be a null pointer). The array size must not be smaller than length. |
| uint16_t length | Valid length of the array, which must not exceed the actual length of the hidRelAxes array. |


