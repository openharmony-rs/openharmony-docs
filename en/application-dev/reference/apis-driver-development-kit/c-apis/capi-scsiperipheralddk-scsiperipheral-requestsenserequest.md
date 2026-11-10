# ScsiPeripheral_RequestSenseRequest

```c
struct ScsiPeripheral_RequestSenseRequest {...}
```

## Overview

Defines the SCSI **REQUEST SENSE** request struct. This command is usually used to obtain device error information.

<!--Device-struct ScsiPeripheral_RequestSenseRequest {...}--><!--Device-struct ScsiPeripheral_RequestSenseRequest {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t allocationLength | Allocation length** field used to specify the size of the buffer prepared by the request initiator (usually the host) for the response data, in bytes. |
| uint8_t control | Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command. |
| uint8_t byte1 | First byte of the SCSI command descriptor block (CDB), which usually contains the operation code and operation group information. |
| uint32_t timeout | Timeout interval, in milliseconds. |


