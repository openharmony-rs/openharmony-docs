# Usb_DeviceArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct Usb_DeviceArray {...} Usb_DeviceArray
```

## Overview

Defines the device ID list, which is used to store the device IDs and device quantity obtained using **OH_Usb_GetDevices**.

**Since**: 18

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t* deviceIds | Pointer to the start address of the device ID array that you have applied for. To avoid excessive memory consumption, the recommended maximum size of the allocated array is generally 128.|
| uint32_t num | Defines the device quantity. Device IDs are obtained by traversing **deviceIds** based on the value of this parameter. If the value is **0**, there is no USB device.|
