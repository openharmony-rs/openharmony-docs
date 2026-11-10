# UsbDeviceMemMap

```c
struct UsbDeviceMemMap {...}
```

## Overview

Defines the device memory map created by calling [OH_Usb_CreateDeviceMemMap](capi-usb-ddk-api-h.md#oh_usb_createdevicememmap). A buffer using the device memory map can provide better data transfer performance.

<!--Device-struct UsbDeviceMemMap {...}--><!--Device-struct UsbDeviceMemMap {...}-End-->

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

**Related module**: [UsbDdk](capi-driver-development-kit-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t * const address | Buffer address. |
| const size_t size | Buffer size, in bytes. The value must be greater than 0. |
| uint32_t offset | Offset of the used buffer. The default value is **0**, indicating that there is no offset. The offset is calculated from the buffer address. The sum of **offset** and **bufferLength** must be less than or equal to **<br>size**. |
| uint32_t bufferLength | Length of the used buffer. By default, the value is equal to the buffer size, indicating that the entire buffer is used. The sum of **offset** and **bufferLength** must be less than or equal to **size**. |
| uint32_t transferedLength | Length of the data actually transferred, in bytes. |


