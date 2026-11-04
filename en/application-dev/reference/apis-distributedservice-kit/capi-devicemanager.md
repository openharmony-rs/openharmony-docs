# DeviceManager
<!--Kit: Distributed Service Kit-->
<!--Subsystem: DistributedSched-->
<!--Owner: @hobbycao;@huangkai71-->
<!--Designer: @gsxiaowen;@lee_jet520-->
<!--Tester: @hanjiawei;@Ytt-test-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=6464d8a99d9b01dc23db63dc129806a3869aade5 translatedAt=2026-11-03T12:57:06.693Z pushedAt=2026-11-04T08:47:59.633Z nl=1 -->

## Overview

This module provides distributed device management capabilities for obtaining basic information about trusted devices and the local device. A trusted device is a device that has established a trust relationship through device authentication. Basic information includes the device name, device type, device identifier, and device status. This module provides functions such as device discovery, device binding, device information query, and device status listening. It applies to scenarios such as distributed cross-device collaboration and device interconnection, enabling service collaboration and data sharing.


Developers can use the APIs provided by this module to obtain device information and complete development tasks related to distributed device management. For details about the module design logic and usage, see [Distributed Device Management Development](../../distributedservice/devicemanager-guidelines.md).

**Since**: 20

## Files

| Name| Description|
| -- | -- |
| [oh_device_manager.h](capi-oh-device-manager-h.md) | Provides APIs to obtain information about trusted devices and local devices. |
| [oh_device_manager_err_code.h](capi-oh-device-manager-err-code-h.md) | Declares the error codes of the distributed device management module. |
