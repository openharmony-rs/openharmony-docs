# UsbDdk
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:12:15.164Z pushedAt=2026-11-10T01:49:31.054Z nl=1 -->

## Overview

Provides USB DDK APIs to open and close USB interfaces, perform non-isochronous and isochronous data transfer over USB pipes, and implement control transfer and interrupt transfer. This module is applicable to scenarios where underlying interaction and data communication with USB devices are required, helping you efficiently develop USB device drivers.

**System capability**: SystemCapability.Driver.USB.Extension

**Since**: 10

## Files

| Name| Description|
| -- | -- |
| [usb_ddk_api.h](capi-usb-ddk-api-h.md) | Declares the USB DDK APIs used by the host to access the device. These APIs provide functions such as USB device management, configuration, and data transmission, helping developers implement underlying interaction and data communication with the USB device. |
| [usb_ddk_types.h](capi-usb-ddk-types-h.md) | Provides the enumeration types and structures used in USB DDK APIs, including core data structures such as USB device description, control transfer, and request pipe, to facilitate driver development. |
