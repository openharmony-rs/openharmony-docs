# ScsiPeripheral_TestUnitReadyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_TestUnitReadyRequest {...} ScsiPeripheral_TestUnitReadyRequest
```

## Overview

Defines the SCSI command (**TEST UNIT READY**) request struct, which is usually used to check whether the logical unit is ready. A logical unit is an I/O operation entity that can be independently addressed in a SCSI device.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t control | **Control** field used to specify the control information of the SCSI command.|
| uint32_t timeout | Timeout interval, in milliseconds.|
