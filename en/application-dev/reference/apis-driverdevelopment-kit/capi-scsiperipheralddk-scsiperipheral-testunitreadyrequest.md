# ScsiPeripheral_TestUnitReadyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:10:28.272Z pushedAt=2026-11-10T01:46:27.541Z nl=1 -->

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
| uint8_t control | Control field, which specifies the control information of the SCSI command. |
| uint32_t timeout | Timeout interval, in milliseconds. |


