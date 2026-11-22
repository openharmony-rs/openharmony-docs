# Hid_EventTypeArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_EventTypeArray {...} Hid_EventTypeArray
```

## Overview

Defines an array of event type codes, which stores information about the event types supported by an HID device.

**Since**: 11

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [Hid_EventType](capi-hid-ddk-types-h.md#hid_eventtype)* hidEventType | Pointer to the array of event type codes, which points to the array pre-allocated by the caller. The pointer cannot be null. The array size must be greater than or equal to the value of length.|
| uint16_t length | Valid length of the array, which cannot exceed the actual length of the **hidEventType** array.|
