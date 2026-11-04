# Hid_DeviceHandle
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T03:41:21.614Z pushedAt=2026-11-04T10:12:49.973Z nl=1 -->

```c
typedef struct Hid_DeviceHandle Hid_DeviceHandle
```

## Overview

An opaque USB HID device struct used to identify and operate HID device instances. Developers use this handle to open, close, read, and write HID devices.

**Since**: 18

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

