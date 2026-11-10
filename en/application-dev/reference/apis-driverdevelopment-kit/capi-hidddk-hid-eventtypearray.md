# Hid_EventTypeArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:09:01.454Z pushedAt=2026-11-10T01:39:41.756Z nl=1 -->

```c
typedef struct Hid_EventTypeArray {...} Hid_EventTypeArray
```

## Overview

Array of event type encodings, used to store the event type information supported by an HID device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Hid_EventType](capi-hid-ddk-types-h.md#hid_eventtype)* hidEventType | Pointer to the event type code array, which points to the array pre-allocated by the caller (must not be a null pointer). The array size is not less than length. |
| uint16_t length | Valid length of the array, which does not exceed the actual length of the hidEventType array. |


