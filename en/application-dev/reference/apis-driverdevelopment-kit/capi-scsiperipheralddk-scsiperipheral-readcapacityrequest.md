# ScsiPeripheral_ReadCapacityRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_ReadCapacityRequest {...} ScsiPeripheral_ReadCapacityRequest
```

## Overview

Defines the SCSI command (**READ CAPACITY**) request struct, which is used to send a command for reading the storage capacity. It helps obtain the logical block size and total number of blocks of a device.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Logical block address, which specifies the start position for reading the capacity. If the value is **0**, the overall capacity of the device is obtained.|
| uint8_t control | **Control** field used to specify the control information of the SCSI command.|
| uint8_t byte8 | Eighth byte of the command descriptor block (CDB).|
| uint32_t timeout | Timeout interval, in milliseconds.|
