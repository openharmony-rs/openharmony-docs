# USBSerialDDK
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6be4fce6dcc641d6f56c59a16ae6449540255825 translatedAt=2026-10-14T04:53:07.393Z pushedAt=2026-10-22T02:20:37.415Z nl=2 -->

## Overview

Provides USB Serial Driver Development Kit (USB Serial DDK) APIs, including the enum types and data structs used by USB Serial DDK APIs. Serial port communication is often used in industrial scenarios and some legacy devices, such as card issuers and ID card readers. By using the USB Serial DDK, you can develop USB serial port peripherals extension drivers.

**System capability**: SystemCapability.Driver.UsbSerial.Extension

**Since**: 18

## Files

| Name| Description|
| -- | -- |
| [usb_serial_api.h](capi-usb-serial-api-h.md) | Declares the USB Serial DDK APIs used by the host to access the serial port device. It provides the capabilities of reading data from and writing data to serial ports and configuring parameters. This API is applicable to scenarios where serial port devices need to be accessed through the USB port, such as industrial control and embedded device communication. |
| [usb_serial_types.h](capi-usb-serial-types-h.md) | Provides the enumeration types and structures used in USB Serial DDK APIs. It is used for USB serial port driver development, simplifying operations such as parameter configuration, return code processing, and flow control for serial port devices, and improving driver development efficiency. |
