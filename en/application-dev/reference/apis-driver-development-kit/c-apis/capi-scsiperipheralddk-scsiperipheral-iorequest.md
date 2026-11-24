# ScsiPeripheral_IORequest

```c
typedef struct ScsiPeripheral_IORequest {...} ScsiPeripheral_IORequest
```

## Overview

Defines the read/write operation request. This struct defines the request parameters required for the SCSI peripheral to perform read/write operations, including the start address of the logical block, transfer length, and control information.

<!--Device-struct ScsiPeripheral_IORequest {...}--><!--Device-struct ScsiPeripheral_IORequest {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t lbAddress | Start address of a logical block, which specifies the start position for read/write operations of the SCSI peripheral.<br><!--Device-uint32_t lbAddress--><!--Device-uint32_t lbAddress-End--> |
| uint16_t transferLength | Number of consecutive logical blocks to be operated. The value must be a positive integer and cannot exceed the maximum number of logical blocks that can be transferred at a time.<br><!--Device-uint16_t transferLength--><!--Device-uint16_t transferLength-End--> |
| uint8_t control | **Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command.<br><!--Device-uint8_t control--><!--Device-uint8_t control-End--> |
| uint8_t byte1 | First byte of the SCSI command descriptor block (CDB), which usually contains the operation code and operation group information.<br><!--Device-uint8_t byte1--><!--Device-uint8_t byte1-End--> |
| uint8_t byte6 | Sixth byte of the SCSI CDB, which contains different parameters or flag information based on the command type.<br><!--Device-uint8_t byte6--><!--Device-uint8_t byte6-End--> |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) *data | Buffer for data transmission.<br><!--Device-ScsiPeripheral_DeviceMemMap *data--><!--Device-ScsiPeripheral_DeviceMemMap *data-End--> |
| uint32_t timeout | Timeout interval, in milliseconds.<br><!--Device-uint32_t timeout--><!--Device-uint32_t timeout-End--> |


