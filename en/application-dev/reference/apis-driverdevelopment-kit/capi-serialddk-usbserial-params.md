# UsbSerial_Params
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct UsbSerial_Params {...} __attribute__((aligned(8))) UsbSerial_Params
```

## Overview

Defines the USB serial port parameters for the USB Serial DDK.

**Since**: 18

**Related module**: [USBSerialDDK](capi-serialddk.md)

**Header file:** [usb_serial_types.h](capi-usb-serial-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t baudRate | Baud rate, in bauds.|
| uint8_t nDataBits | Number of data bits.|
| uint8_t nStopBits | Number of stop bits.|
| uint8_t parity | Parity parameter setting. **0**: no parity; **1**: odd parity; **2**: even parity; **3**: mark parity (parity bit always 1); **4**: space parity (parity bit always 0)|
