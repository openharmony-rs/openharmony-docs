# Usb_DeviceArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=4e4b18ce5c3346ee05b620e87051d886ec217a55 translatedAt=2026-10-14T04:55:28.432Z pushedAt=2026-10-22T03:14:00.468Z nl=2 -->

```c
typedef struct Usb_DeviceArray {...} Usb_DeviceArray
```

## Overview

Defines the device ID array, which is used to store the device IDs and device quantity obtained using [OH_Usb_GetDevices](capi-usb-ddk-api-h.md#oh_usb_getdevices). After using the structure, you must release the memory allocated for the device ID array. Otherwise, resource leaks may occur.

**Since**: 18

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file:** [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint64_t* deviceIds | Pointer to the start address of the device ID array that you have applied for. To avoid excessive memory consumption, it is recommended that the maximum size of the allocated array be 128. |
| uint32_t num | Device quantity. Device IDs are obtained by traversing **deviceIds** based on the value of this parameter. If the value is **0**, there is no USB device.|


