# ScsiPeripheral_DeviceMemMap
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

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
| uint8_t* const address | Start address of the buffer mapped to the device memory, pointing to the mapped device memory space. This buffer is used to store SCSI device data and provides high-performance memory access capabilities.|
| const size_t size | Buffer size, in bytes. The value must be greater than 0.|
| uint32_t offset | Read/write start offset of the buffer, in bytes. The default value is **0**, indicating that there is no offset and the buffer starts from the specified address. The value range is [0, **size**]. Set this parameter when you need to start reading/writing data from a specific position in the buffer. Different offset values correspond to different start positions for reading/writing.|
| uint32_t bufferLength | Length of the used buffer, in bytes. By default, the value is equal to the size of the buffer, indicating that the entire buffer is used. Set this parameter when only a part of the buffer is used. The sum of **bufferLength** and **offset** must be less than or equal to the value of **size**.|
| uint32_t transferredLength | Length of the transferred data, in bytes. The initial value is **0**, indicating that no data has been transferred. This field is updated after SCSI data transfer is complete. It indicates the actual amount of data transferred and can be used to monitor the transfer progress.|
