# UsbRequestPipe

```c
typedef struct UsbRequestPipe {...} __attribute__((aligned(8))) UsbRequestPipe
```

## Overview

Defines a USB request pipe.

**Since**: 10

**Related module**: [UsbDdk](capi-usbddk.md)

**Header file**: [usb_ddk_types.h](capi-usb-ddk-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint64_t interfaceHandle | Interface operation handle. |
| uint32_t timeout | Timeout duration, in milliseconds. |
| uint8_t endpoint | Endpoint address. |


