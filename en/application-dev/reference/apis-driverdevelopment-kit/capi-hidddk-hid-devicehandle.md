# Hid_DeviceHandle
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:08:50.997Z pushedAt=2026-11-10T01:39:25.428Z nl=1 -->

```c
typedef struct Hid_DeviceHandle Hid_DeviceHandle
```

## Overview

Opaque USB HID device struct, used to identify and operate an HID device instance. You can use this handle to open, close, read, and write an HID device.

**Since**: 18

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)

