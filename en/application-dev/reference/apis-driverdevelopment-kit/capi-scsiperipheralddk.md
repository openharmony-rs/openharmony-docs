# ScsiPeripheralDDK
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:49:05.580Z pushedAt=2026-06-22T11:21:11.414Z -->

## Overview

The SCSI Peripheral DDK is a suite dedicated to SCSI device driver development at the application layer. It provides APIs for initializing the DDK, releasing the DDK, enabling and disabling devices, and reading data from and writing data to devices. It also declares the macros, enum variables, and data structures required by the SCSI Peripheral DDK APIs.

**Since**: 18

## Files

| Name| Description|
| -- | -- |
| [scsi_peripheral_api.h](capi-scsi-peripheral-api-h.md) | Declares the SCSI Peripheral DDK APIs used by the host to access the SCSI device.|
| [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md) | Provides the enum variables, structures, and macros used in the SCSI Peripheral DDK APIs.|