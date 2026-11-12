# ScsiPeripheral_VerifyRequest

```c
typedef struct ScsiPeripheral_VerifyRequest {...} ScsiPeripheral_VerifyRequest
```

## Overview

Defines the SCSI command (**VERIFY**) request struct, which is usually used to verify the data integrity of logical blocks.

<!--Device-struct ScsiPeripheral_VerifyRequest {...}--><!--Device-struct ScsiPeripheral_VerifyRequest {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t lbAddress | Start address of logical blocks. |
| uint16_t verificationLength | Number of consecutive logical blocks to be verified. |
| uint8_t control | Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command. |
| uint8_t byte1 | First byte of the SCSI command descriptor block (CDB), which usually contains the operation code and operation group information. |
| uint8_t byte6 | Sixth byte of the SCSI CDB, which contains different parameters or flag information based on the command type. |
| uint32_t timeout | Timeout interval, in milliseconds. |


