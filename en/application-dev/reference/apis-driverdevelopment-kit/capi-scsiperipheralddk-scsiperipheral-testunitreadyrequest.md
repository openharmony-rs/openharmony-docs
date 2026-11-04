# ScsiPeripheral_TestUnitReadyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-04T03:54:37.333Z pushedAt=2026-11-04T10:12:50.013Z nl=1 -->

```c
typedef struct ScsiPeripheral_TestUnitReadyRequest {...} ScsiPeripheral_TestUnitReadyRequest
```

## Overview

Request struct for the SCSI command (TEST UNIT READY), which is typically used to check whether a logical unit is ready (a logical unit is an independently addressable I/O operation entity in a SCSI device).

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t control | Control field, used to specify the control information of the SCSI command. |
| uint32_t timeout | Timeout interval, in milliseconds. |


