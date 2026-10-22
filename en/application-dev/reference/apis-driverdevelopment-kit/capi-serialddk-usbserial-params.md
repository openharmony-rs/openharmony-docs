# UsbSerial_Params
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=4e4b18ce5c3346ee05b620e87051d886ec217a55 translatedAt=2026-10-14T04:52:58.409Z pushedAt=2026-10-22T02:08:47.623Z nl=2 -->

```c
typedef struct UsbSerial_Params {...} __attribute__((aligned(8))) UsbSerial_Params
```

## Overview

Defines the USB serial port parameters for the USB Serial DDK, which are used for configuring the communication parameters of the USB-to-serial device. The parameter configuration must be consistent with that of the target communication device. Otherwise, the communication may fail. It is commonly used in scenarios where communication with devices through the USB serial port is required, such as industrial control devices, debugging tools, and sensor data collection.

**Since**: 18

**Related module**: [USBSerialDDK](capi-serialddk.md)

**Header file:** [usb_serial_types.h](capi-usb-serial-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t baudRate | Baud rate, unit: baud. |
| uint8_t nDataBits | Number of data bits.|
| uint8_t nStopBits | Number of stop bits.|
| uint8_t parity | Parity setting (0: no parity; 1: odd parity; 2: even parity). |


