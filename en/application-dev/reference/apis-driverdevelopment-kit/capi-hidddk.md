# HidDdk
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=ef68d0fccde41b2177fb89718c471fa052677a04 translatedAt=2026-11-10T01:09:20.535Z pushedAt=2026-11-10T01:41:01.755Z nl=1 -->

## Overview

Provides the HID DDK APIs for creating devices, sending events, and destroying devices, which can be used in driver development of HID devices.

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

## Files

| Name| Description|
| -- | -- |
| [hid_ddk_api.h](capi-hid-ddk-api-h.md) | Declares the HID DDK (Driver Development Kit) APIs for accessing input devices on the host side. This module provides the capabilities of creating, opening, reading from, and writing to HID devices, and supports device management and event injection. It supports two usage modes: one is the creation of virtual HID devices and event injection, applicable to scenarios such as simulating keyboard, mouse, and touchscreen input; the other is the access to and communication with real HID devices, supporting opening devices, reading and writing device reports, and obtaining device information, applicable to scenarios of data interaction with HID devices. |
| [hid_ddk_types.h](capi-hid-ddk-types-h.md) | Provides the enum variables and struct definitions in the HID DDK, supporting developers in defining and operating HID devices during driver development. It is suitable for scenarios involving interaction with input devices such as mouse, keyboard, and touchscreen, and provides complete definitions of device features, event types, key codes, and coordinate axes, helping developers quickly implement driver development for HID devices. |
