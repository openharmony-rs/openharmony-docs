# ScsiPeripheral_RequestSenseRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_RequestSenseRequest {...} ScsiPeripheral_RequestSenseRequest
```

## Overview

Defines the SCSI **REQUEST SENSE** request struct. This command is usually used to obtain device error information.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t allocationLength | **Allocation length** field used to specify the size of the buffer prepared by the request initiator (usually the host) for the response data. The unit is byte.|
| uint8_t control | **Control** field used to specify the control information of the SCSI command.|
| uint8_t byte1 | First byte of the command descriptor block (CDB).|
| uint32_t timeout | Timeout interval, in milliseconds.|
