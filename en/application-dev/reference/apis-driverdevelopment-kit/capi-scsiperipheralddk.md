# ScsiPeripheralDDK
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-04T03:56:04.155Z pushedAt=2026-11-04T10:12:50.018Z nl=1 -->

## Overview

SCSI Peripheral DDK is a kit designed for developers to develop SCSI device drivers. It provides APIs for initializing the DDK, releasing the DDK, opening and closing devices, and reading from and writing to devices, and declares the macros, enum variables, and data structures required for developing SCSI device drivers. Its use cases include storage device driver development and disk array management.

**Since**: 18

## Files

| Name| Description|
| -- | -- |
| [scsi_peripheral_api.h](capi-scsi-peripheral-api-h.md) | Declares the SCSI Peripheral DDK APIs for accessing SCSI devices from the host side. This module is based on the SCSI protocol standard and provides SCSI device access capabilities through DDK driver services. |
| [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md) | Provides the enum variables, structures, and macros used in the SCSI Peripheral DDK APIs.|
