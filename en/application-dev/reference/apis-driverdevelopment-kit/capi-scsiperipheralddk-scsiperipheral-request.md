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

Defines the SCSI request parameters. It is Defines the request structure.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| uint8_t commandDescriptorBlock[[SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN](capi-scsi-peripheral-types-h.md#macros)] | Command descriptor block. |
| uint8_t cdbLength | Length of the command descriptor block. Ensure that the length matches the actual command. The maximum length cannot exceed [SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN](capi-scsi-peripheral-types-h.md#macros). |
| int8_t dataTransferDirection | Data transfer direction: **–1** indicates no data transfer, **–2** indicates data transfer (write) from the host to the device, **–3** indicates data transfer (read) from the device to the host, and **–4** indicates bidirectional data transfer. |
| ScsiPeripheral_DeviceMemMap* data | Buffer for data transmission. |
| uint32_t timeout | Timeout duration, in ms. |


