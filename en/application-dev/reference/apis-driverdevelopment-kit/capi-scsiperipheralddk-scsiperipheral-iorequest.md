# ScsiPeripheral_IORequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-04T03:51:43.873Z pushedAt=2026-11-04T10:12:50.006Z nl=1 -->

```c
typedef struct ScsiPeripheral_IORequest {...} ScsiPeripheral_IORequest
```

## Overview

Request parameters for read/write operations. This struct defines the request parameters required for read/write operations on a SCSI peripheral, including the logical block start address, transfer length, and control information.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Start logical block address, which specifies the start logical block position of the SCSI peripheral read/write operation. |
| uint16_t transferLength | Number of consecutive logical blocks to operate on. The value must be a positive integer and must not exceed the maximum number of logical blocks that the device can transfer in a single operation. |
| uint8_t control | Control field, which specifies the control flags of the SCSI command, such as priority and linked command options. |
| uint8_t byte1 | First byte of the SCSI Command Descriptor Block (CDB), which usually contains the operation code and operation group information. |
| uint8_t byte6 | Sixth byte of the SCSI Command Descriptor Block (CDB), which contains different parameters or flag information depending on the command type. |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | Buffer for data transmission.|
| uint32_t timeout | Timeout interval, in milliseconds. |


