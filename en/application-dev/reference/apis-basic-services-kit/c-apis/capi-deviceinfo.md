# DeviceInfo

## Overview

Provides APIs for querying terminal device information. This module provides the capability of obtaining basic device information, such as the device type, manufacturer, brand, model, and version. It can be used to adapt device features, collect device information, or manage devices. These APIs obtain device information by reading system properties. The return value is a pointer to a constant string. The pointer points to the data stored in the system. The caller does not need to release the memory.

**System capability**: SystemCapability.Startup.SystemInfo

**Since**: 10

## Files

| Name | Description |
| -- | -- |
| [deviceinfo.h](capi-deviceinfo-h.md) | Declares the APIs for querying device information. This module provides the capability of obtaining basic device information, such as the device type, manufacturer, brand, model, and version. It can be used to adapt device features, collect device information, or manage devices. These APIs obtain device information by reading system properties. The return value is a pointer to a constant string. The pointer points to the data stored in the system. The caller does not need to release the memory. |
