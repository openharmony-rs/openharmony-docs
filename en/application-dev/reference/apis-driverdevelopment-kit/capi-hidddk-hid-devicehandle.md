# Hid_DeviceHandle
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct Hid_DeviceHandle Hid_DeviceHandle
```

## Overview

Defines the opaque USB HID device structure, which is used to identify and operate HID device instances. You can use this handle to open, close, read, and write HID devices.

**Since**: 18

**Related module**: [HidDdk](capi-hidddk.md)

**Header file:** [hid_ddk_types.h](capi-hid-ddk-types-h.md)