# ScsiPeripheral_TestUnitReadyRequest

```c
typedef struct ScsiPeripheral_TestUnitReadyRequest {...} ScsiPeripheral_TestUnitReadyRequest
```

## Overview

Defines the request structure of the **test unit ready** command.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t control | Control** field used to specify control information. |
| uint32_t timeout | Timeout duration, in ms. |


