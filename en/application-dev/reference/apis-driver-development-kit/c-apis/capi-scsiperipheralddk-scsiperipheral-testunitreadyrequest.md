# ScsiPeripheral_TestUnitReadyRequest

```c
struct ScsiPeripheral_TestUnitReadyRequest {...}
```

## Overview

Defines the SCSI command (**TEST UNIT READY**) request struct, which is usually used to check whether the logical unit is ready. A logical unit is an I/O operation entity that can be independently addressed in a SCSI device.

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-others-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t control | Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command. |
| uint32_t timeout | Timeout interval, in milliseconds. |


