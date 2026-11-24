# ScsiPeripheral_CapacityInfo

```c
typedef struct ScsiPeripheral_CapacityInfo {...} ScsiPeripheral_CapacityInfo
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
| uint32_t lbAddress | Logical block address returned, indicating the number of the last addressable logical block. The total number of logical blocks is the value of this parameter plus 1.<br><!--Device-uint32_t lbAddress--><!--Device-uint32_t lbAddress-End--> |
| uint32_t lbLength | Length of a single logical unit, in bytes. Size of each logical block, in bytes. The value is usually a standard value such as **512**, **2048**, or **4096**, depending on the device type and formatting mode.<br><!--Device-uint32_t lbLength--><!--Device-uint32_t lbLength-End--> |


