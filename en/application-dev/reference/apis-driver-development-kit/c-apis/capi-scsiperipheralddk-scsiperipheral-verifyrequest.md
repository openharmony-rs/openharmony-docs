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
| uint32_t lbAddress | Start address of logical blocks.<br><!--Device-uint32_t lbAddress--><!--Device-uint32_t lbAddress-End--> |
| uint16_t verificationLength | Number of consecutive logical blocks to be verified.<br><!--Device-uint16_t verificationLength--><!--Device-uint16_t verificationLength-End--> |
| uint8_t control | **Control** field used to specify the control information of the SCSI command.<br><!--Device-uint8_t control--><!--Device-uint8_t control-End--> |
| uint8_t byte1 | First byte of the command descriptor block (CDB).<br><!--Device-uint8_t byte1--><!--Device-uint8_t byte1-End--> |
| uint8_t byte6 | Sixth byte of the CDB.<br><!--Device-uint8_t byte6--><!--Device-uint8_t byte6-End--> |
| uint32_t timeout | Timeout interval, in milliseconds.<br><!--Device-uint32_t timeout--><!--Device-uint32_t timeout-End--> |


