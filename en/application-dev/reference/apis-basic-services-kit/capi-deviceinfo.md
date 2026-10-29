# DeviceInfo
<!--Kit: Basic Services Kit-->
<!--Subsystem: Startup-->
<!--Owner: @chenjinxiang3-->
<!--Designer: @chenjinxiang3-->
<!--Tester: @liuhaonan2-->
<!--Adviser: @fang-jinxu-->
<!-- md-trans-meta sourceCommit=18ebccb19720171b0da7ac54990b23c06c705837 translatedAt=2026-10-09T11:30:53.301Z pushedAt=2026-10-10T03:33:38.347Z -->

## Overview

Provides APIs for querying device information. This module provides the capability of obtaining basic device information, such as the device type, manufacturer, brand, model, and version. It can be used to adapt device features, collect device information, or manage devices. These APIs obtain device information by reading system properties. The return value is a pointer to a constant string. The pointer points to the data stored in the system. The caller does not need to release the memory.

**Since**: 10
## Files

| Name| Description|
| -- | -- |
| [deviceinfo.h](capi-deviceinfo-h.md) | This module provides the capability of obtaining basic device information, such as the device type, manufacturer, brand, model, and version. It can be used to adapt device features, collect device information, or manage devices. These APIs obtain device information by reading system properties. The return value is a pointer to a constant string. The pointer points to the data stored in the system. The caller does not need to release the memory. |