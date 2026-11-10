# UsbSerial_Params

```c
struct UsbSerial_Params {...}
```

## Overview

Defines the USB serial port parameters for the USB Serial DDK, which are used for configuring the communication parameters of the USB-to-serial device. The parameter configuration must be consistent with that of the target communication device. Otherwise, the communication may fail. It is commonly used in scenarios where communication with devices through the USB serial port is required, such as industrial control devices, debugging tools, and sensor data collection.

<!--Device-struct UsbSerial_Params {...}--><!--Device-struct UsbSerial_Params {...}-End-->

**System capability**: SystemCapability.Driver.UsbSerial.Extension

**Since**: 18

**Related module**: [USBSerialDDK](capi-driver-development-kit-usbserialddk.md)

**Header file**: [usb_serial_types.h](capi-usb-serial-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t baudRate | Baud rate, unit: baud. |
| uint8_t nDataBits | Number of data bits. |
| uint8_t nStopBits | Number of stop bits. |
| uint8_t parity | Parity setting (0: no parity; 1: odd parity; 2: even parity). |


