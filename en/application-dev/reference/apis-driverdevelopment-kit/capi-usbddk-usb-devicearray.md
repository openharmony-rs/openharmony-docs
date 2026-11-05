# Usb_DeviceArray
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T04:00:32.388Z pushedAt=2026-11-04T10:12:50.027Z nl=1 -->

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
| uint32_t num | Defines the device quantity. Device IDs are obtained by traversing **deviceIds** based on the value of this parameter. If the value is **0**, there is no USB device.|


