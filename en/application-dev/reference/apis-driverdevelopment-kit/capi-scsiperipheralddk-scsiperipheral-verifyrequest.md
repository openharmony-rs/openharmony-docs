# ScsiPeripheral_VerifyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_VerifyRequest {...} ScsiPeripheral_VerifyRequest
```

## Overview

Defines the SCSI command (**VERIFY**) request struct, which is usually used to verify the data integrity of logical blocks.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Start address of logical blocks.|
| uint16_t verificationLength | Number of consecutive logical blocks to be verified.|
| uint8_t control | **Control** field used to specify the control information of the SCSI command.|
| uint8_t byte1 | First byte of the command descriptor block (CDB).|
| uint8_t byte6 | Sixth byte of the CDB.|
| uint32_t timeout | Timeout interval, in milliseconds.|
