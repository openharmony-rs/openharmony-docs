# ScsiPeripheral_ReadCapacityRequest

```c
struct ScsiPeripheral_ReadCapacityRequest {...}
```

## Overview

Defines the SCSI command (**READ CAPACITY**) request struct, which is used to send a command for reading the storage capacity. It helps obtain the logical block size and total number of blocks of a device.

<!--Device-struct ScsiPeripheral_ReadCapacityRequest {...}--><!--Device-struct ScsiPeripheral_ReadCapacityRequest {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t lbAddress | Logical block address, which specifies the start position for reading the capacity. If the value is **0**, the overall capacity of the device is obtained. |
| uint8_t control | Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command. |
| uint8_t byte8 | Eighth byte of the command descriptor block (CDB). |
| uint32_t timeout | Timeout interval, in milliseconds. |


