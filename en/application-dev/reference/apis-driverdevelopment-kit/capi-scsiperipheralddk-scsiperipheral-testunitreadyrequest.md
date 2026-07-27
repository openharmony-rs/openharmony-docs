# ScsiPeripheral_TestUnitReadyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:48:57.296Z pushedAt=2026-06-22T11:21:11.413Z -->

```c
typedef struct ScsiPeripheral_TestUnitReadyRequest {...} ScsiPeripheral_TestUnitReadyRequest
```

## Overview

Defines the request structure of the **test unit ready** command.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t control | **Control** field used to specify control information.|
| uint32_t timeout | Timeout duration, in ms.|