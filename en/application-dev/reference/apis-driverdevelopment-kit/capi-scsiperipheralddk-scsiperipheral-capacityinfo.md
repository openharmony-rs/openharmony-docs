# ScsiPeripheral_CapacityInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:09:37.225Z pushedAt=2026-11-10T01:44:05.222Z nl=1 -->

```c
typedef struct ScsiPeripheral_CapacityInfo {...} ScsiPeripheral_CapacityInfo
```

## Overview

Defines the **SCSI READ CAPACITY** struct. This method can be used to obtain the storage capacity information of a device when developing a SCSI device driver. It supports operations such as partition management, available space check, and storage resource allocation.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Returned logical block address, which indicates the number of the last addressable logical block. The total number of logical blocks is this value plus 1. |
| uint32_t lbLength | Length of a single logical block (unit: Byte). Indicates the byte size of each logical block, which is usually a standard value such as 512, 2048, or 4096, depending on the device type and formatting method. |


