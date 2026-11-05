# DeviceManager
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @liwei_hw-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=4feb11911c08e98492628e7f5d7f92f9929a4a7f translatedAt=2026-11-03T10:53:27.960Z pushedAt=2026-11-03T11:16:29.622Z nl=1 -->

## Overview

This module provides distributed device management capabilities for obtaining basic information about trusted devices and the local device. A trusted device is a device that has established a trust relationship through device authentication. Basic information includes the device name, device type, device identifier, and device status. This module provides functions such as device discovery, device binding, device information query, and device status listening. It applies to scenarios such as distributed cross-device collaboration and device interconnection, enabling service collaboration and data sharing.


Developers can use the APIs provided by this module to obtain device information and complete development tasks related to distributed device management. For details about the module design logic and usage, see [Distributed Device Management Development](../../distributedservice/devicemanager-guidelines.md).

**Since**: 20

## Files

| Name| Description|
| -- | -- |
| [oh_device_manager.h](capi-oh-device-manager-h.md) | Provides APIs for accessing trusted device and local device information. |
| [oh_device_manager_err_code.h](capi-oh-device-manager-err-code-h.md) | Declares the error codes of the device management module. |
