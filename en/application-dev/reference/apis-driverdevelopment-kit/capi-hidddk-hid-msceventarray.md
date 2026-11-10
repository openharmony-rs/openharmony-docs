# Hid_MscEventArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:09:08.345Z pushedAt=2026-11-10T01:39:59.068Z nl=1 -->

```c
typedef struct Hid_MscEventArray {...} Hid_MscEventArray
```

## Overview

Array of other special event attributes, used to store the special event information supported by the HID device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Hid_MscEvent](capi-hid-ddk-types-h.md#hid_mscevent)* hidMscEvent | Pointer to the array of other special event attribute codes. The array is pre-allocated by the caller (must not be a null pointer), and its size is not less than length. |
| uint16_t length | Valid length of the array, which does not exceed the actual length of the hidMscEvent array. |


