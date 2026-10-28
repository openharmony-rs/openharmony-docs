# ScsiPeripheral_IORequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_IORequest {...} ScsiPeripheral_IORequest
```

## Overview

Defines the read/write operation request. This struct defines the request parameters required for the SCSI peripheral to perform read/write operations, including the start address of the logical block, transfer length, and control information.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Start address of a logical block, which specifies the start position for read/write operations of the SCSI peripheral.|
| uint16_t transferLength | Number of consecutive logical blocks to be operated. The value must be a positive integer and cannot exceed the maximum number of logical blocks that can be transferred at a time.|
| uint8_t control | **Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command.|
| uint8_t byte1 | First byte of the SCSI command descriptor block (CDB), which usually contains the operation code and operation group information.|
| uint8_t byte6 | Sixth byte of the SCSI CDB, which contains different parameters or flag information based on the command type.|
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | Buffer for data transmission.|
| uint32_t timeout | Timeout interval, in milliseconds.|
