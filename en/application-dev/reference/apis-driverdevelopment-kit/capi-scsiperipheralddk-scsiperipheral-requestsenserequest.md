# ScsiPeripheral_RequestSenseRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-04T03:53:05.934Z pushedAt=2026-11-04T10:12:50.009Z nl=1 -->

```c
typedef struct ScsiPeripheral_RequestSenseRequest {...} ScsiPeripheral_RequestSenseRequest
```

## Overview

Request structure of the SCSI command (REQUEST SENSE), which is typically used to obtain device error information.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t allocationLength | Allocation length field, which specifies the size of the buffer prepared by the request initiator (usually the host) for the response data, in bytes. |
| uint8_t control | Control field, which specifies the control information of the SCSI command. |
| uint8_t byte1 | First byte of the CDB (Command Descriptor Block). |
| uint32_t timeout | Timeout interval, in milliseconds. |


