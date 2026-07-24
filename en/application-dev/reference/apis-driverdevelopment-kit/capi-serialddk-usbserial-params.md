# UsbSerial_Params
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:49:08.527Z pushedAt=2026-06-22T11:21:11.417Z -->

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
| uint8_t parity | Parity parameter setting. **0**: no parity; **1**: odd parity; **2**: even parity. |