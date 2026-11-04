# DeviceManager
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @liwei_hw-->
<!--Designer: @hwzhangchuang-->
<!--Tester: @zhaodengqi-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b58a7e7503b87d2e69397d1a6f5f0633f3249623 translatedAt=2026-11-04T05:12:09.555Z pushedAt=2026-11-04T10:12:33.541Z nl=1 -->

## Overview

This module provides distributed device management capabilities for obtaining basic information about trusted devices and the local device. A trusted device is a device that has established a trust relationship through device authentication. Basic information includes the device name, device type, device identifier, and device status. This module provides functions such as device discovery, device binding, device information query, and device status listening. It applies to scenarios such as distributed cross-device collaboration and device interconnection, enabling service collaboration and data sharing.


Developers can use the APIs provided by this module to obtain device information and complete development tasks related to distributed device management. For details about the module design logic and usage, see [Distributed Device Management Development](../../distributedservice/devicemanager-guidelines.md).

**Since**: 20

## Files

| Name| Description|
| -- | -- |
| [oh_device_manager.h](capi-oh-device-manager-h.md) | Provides APIs to obtain information about trusted devices and local devices. |
| [oh_device_manager_err_code.h](capi-oh-device-manager-err-code-h.md) | Declares the error codes of the distributed device management module. |
