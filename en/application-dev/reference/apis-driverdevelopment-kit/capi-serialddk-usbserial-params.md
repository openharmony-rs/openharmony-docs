# UsbSerial_Params

<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a16dcd5380f352b729da625973de1c33bd7c6a2a translatedAt=2026-06-10T11:03:24.132Z pushedAt=2026-06-11T03:41:56.085Z -->

```c
typedef struct UsbSerial_Params {...} __attribute__((aligned(8))) UsbSerial_Params
```

## Overview

Defines the USB serial port parameters for the USB SERIAL DDK.

**Since**: 18

**Related module**: [USBSerialDDK](capi-serialddk.md)

**Header file:** [usb_serial_types.h](capi-usb-serial-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t baudRate | Baud rate.|
| uint8_t nDataBits | Number of data transfer bits.|
| uint8_t nStopBits | Number of data stop bits.|
| uint8_t parity | Parity parameter setting. **0**: no parity; **1**: odd parity; **2**: even parity. |