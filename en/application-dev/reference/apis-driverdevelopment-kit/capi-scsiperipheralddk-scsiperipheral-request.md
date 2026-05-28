# ScsiPeripheral_Request
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct ScsiPeripheral_Request {...} ScsiPeripheral_Request
```

## Overview

Defines the request structure.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t commandDescriptorBlock[[SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN](capi-scsi-peripheral-types-h.md#scsiperipheral_max_cmd_desc_block_len)] | Command descriptor block.|
| uint8_t cdbLength | Length of the command descriptor block.|
| int8_t dataTransferDirection | Data transfer direction: **–1** indicates no data transfer, **–2** indicates data transfer (write) from the host to the device, **–3** indicates data transfer (read) from the device to the host, and **–4** indicates bidirectional data transfer.|
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | Buffer for data transmission.|
| uint32_t timeout | Timeout duration, in ms.|
