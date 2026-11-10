# ScsiPeripheral_VerifyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:10:37.627Z pushedAt=2026-11-10T01:46:31.126Z nl=1 -->

```c
typedef struct ScsiPeripheral_VerifyRequest {...} ScsiPeripheral_VerifyRequest
```

## Overview

Request struct for the SCSI VERIFY command, which is typically used to verify the data integrity of logical blocks.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Start address of logical blocks.|
| uint16_t verificationLength | Number of consecutive logical blocks to be verified. |
| uint8_t control | Control field, which specifies the control information of the SCSI command. |
| uint8_t byte1 | First byte of the CDB (Command Descriptor Block). |
| uint8_t byte6 | Sixth byte of the CDB (Command Descriptor Block). |
| uint32_t timeout | Timeout interval, in milliseconds. |


