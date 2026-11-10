# ScsiPeripheral_ReadCapacityRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:10:10.862Z pushedAt=2026-11-10T01:45:34.919Z nl=1 -->

```c
typedef struct ScsiPeripheral_ReadCapacityRequest {...} ScsiPeripheral_ReadCapacityRequest
```

## Overview

Defines the request struct for the **SCSI READ CAPACITY** command, which is used to send a command for reading the storage capacity and helps obtain the logical block size and total number of blocks of the device.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Logical block address, which specifies the starting logical block position for reading the capacity. When the value is 0, the overall capacity information of the device is obtained. |
| uint8_t control | Control field, which specifies the control information of the SCSI command. |
| uint8_t byte8 | The eighth byte of the CDB (Command Descriptor Block). |
| uint32_t timeout | Timeout interval, in milliseconds. |


