# USBSerialDDK

## Overview

Provides USB SERIAL DDK types and declares the macros, enumerated variables, and data structures required by the USB SERIAL DDK APIs.

**System capability**: SystemCapability.Driver.UsbSerial.Extension

**Since**: 18

## Files

| Name | Description |
| -- | -- |
| [usb_serial_api.h](capi-usb-serial-api-h.md) | Declares the USB Serial DDK APIs used by the host to access the serial port device. It provides the capabilities of reading data from and writing data to serial ports and configuring parameters. This API is applicable to scenarios where serial port devices need to be accessed through the USB port, such as industrial control and embedded device communication. |
| [usb_serial_types.h](capi-usb-serial-types-h.md) | Provides the enumeration types and structures used in USB Serial DDK APIs. It is used for USB serial port driver development, simplifying operations such as parameter configuration, return code processing, and flow control for serial port devices, and improving driver development efficiency. |
