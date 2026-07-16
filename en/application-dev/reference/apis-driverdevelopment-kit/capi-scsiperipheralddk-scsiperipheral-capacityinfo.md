# ScsiPeripheral_CapacityInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:48:27.845Z pushedAt=2026-06-22T11:21:11.395Z -->

```c
typedef struct ScsiPeripheral_CapacityInfo {...} ScsiPeripheral_CapacityInfo
```

## Overview

Defines the SCSI read capacity.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint32_t lbAddress | Address of the logical unit.|
| uint32_t lbLength | Length of a single logical unit, in bytes.|