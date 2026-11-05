# HidDdk

## Overview

Provides HID DDK interfaces, including creating a device, sending an event, and destroying a device.

**System capability**: SystemCapability.Driver.HID.Extension

**Since**: 11

## Files

| Name | Description |
| -- | -- |
| [hid_ddk_types.h](capi-hid-ddk-types-h.md) | Defines the enum variables and structs used in the HID DDK, allowing you to define and operate HID devices during driver development. This module is applicable to scenarios where input devices such as the mouse, keyboard, and touchscreen are used. It provides comprehensive definitions of device features, event types, key value encoding, and coordinate axes, helping you quickly develop drivers for HID devices. |
| [hid_ddk_api.h](capi-hid-ddk-api-h.md) | Declares the HID DDK functions for accessing an input device from the host. DDK stands for Driver Development Kit. This module provides APIs for creating, opening, reading data from, and writing data to HID devices, as well as managing devices and injecting events. It supports two use modes. The first one is creating virtual HID devices and injecting events, which is suitable for simulating keyboard, mouse, and touchscreen inputs. The second one is accessing and communicating with real HID devices, which allows you to open, read, and write device reports and obtain device information. The second mode is applicable to scenarios where data interaction with HID devices is required. |
