# ScsiPeripheral_DeviceMemMap
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:09:51.885Z pushedAt=2026-11-10T01:44:38.671Z nl=1 -->

```c
typedef struct ScsiPeripheral_DeviceMemMap {...} ScsiPeripheral_DeviceMemMap
```

## Overview

Represents the device memory mapping created by calling [OH_ScsiPeripheral_CreateDeviceMemMap](capi-scsi-peripheral-api-h.md#oh_scsiperipheral_createdevicememmap). The buffer that uses the device memory mapping can provide better performance.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t* const address | Starting address of the buffer in the device memory map, which points to the mapped device memory space. This buffer is used to store SCSI device data and provides high-performance memory access. |
| const size_t size | Buffer size, in bytes. The value must be greater than 0. |
| uint32_t offset | Starting offset for reading from and writing to the buffer, in bytes. The default value is 0, which means no offset and the buffer starts from the specified address. The value ranges from 0 to size. Set this parameter when reading from or writing to a specific position in the buffer. Different offset values correspond to different starting read/write positions. |
| uint32_t bufferLength | Length of the buffer to be used, in bytes. By default, this value equals the buffer size, which means the entire buffer is used. Set this parameter when only part of the buffer is used. The sum of bufferLength and offset must be less than or equal to size. |
| uint32_t transferredLength | Length of the transferred data, in bytes. The initial value is 0, which means no data has been transferred. This field is updated after SCSI data transfer is complete and indicates the actual amount of data transferred. It can be used to monitor the transfer progress. |


