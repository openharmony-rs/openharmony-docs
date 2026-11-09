# ScsiPeripheral_CapacityInfo

```c
struct ScsiPeripheral_CapacityInfo {...}
```

## Overview

Defines the SCSI **READ CAPACITY** struct. It is used to obtain the storage capacity of a device during SCSI driver development. It supports operations such as partition management, available space check, and store resource allocation.

<!--Device-struct ScsiPeripheral_CapacityInfo {...}--><!--Device-struct ScsiPeripheral_CapacityInfo {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t lbAddress | Logical block address, which specifies the start position for reading the capacity. If the value is **0**, the overall capacity of the device is obtained. |
| uint32_t lbLength | Length of a single logical unit, in bytes. Size of each logical block, in bytes. The value is usually a standard value such as **512**, **2048**, or **4096**, depending on the device type and formatting mode. |


