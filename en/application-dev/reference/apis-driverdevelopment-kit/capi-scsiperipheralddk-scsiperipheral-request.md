# ScsiPeripheral_Request
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=eb044167d4199cde694cb11a9d2ff72f155fd2c6 translatedAt=2026-10-29T12:25:36.393Z pushedAt=2026-10-30T07:57:13.298Z nl=1 -->

```c
typedef struct ScsiPeripheral_Request {...} ScsiPeripheral_Request
```

## Overview

Defines the SCSI request parameters. It is used to construct the request parameters for interacting with SCSI devices, including the CDB, data buffer, and timeout interval.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t commandDescriptorBlock[[SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN](capi-scsi-peripheral-types-h.md#macros)] | Command descriptor block, which must comply with the SCSI command specifications. The value must be in a standard descriptor format of the corresponding command. |
| uint8_t cdbLength | Length of the command descriptor block. Ensure that the length matches the actual command. The maximum length cannot exceed [SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN](capi-scsi-peripheral-types-h.md#macros). |
| int8_t dataTransferDirection | Data transfer direction: **–1** indicates no data transfer, **–2** indicates data transfer (write) from the host to the device, **–3** indicates data transfer (read) from the device to the host, and –4 indicates bidirectional data transfer. |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | Pointer to the data transfer buffer. |
| uint32_t timeout | Timeout interval, in milliseconds. |


