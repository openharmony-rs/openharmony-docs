# ScsiPeripheral_BasicSenseInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=a30d46aa87725f954a8669c5a6106a0f5fa2de6d translatedAt=2026-06-22T10:48:31.223Z pushedAt=2026-06-22T11:21:11.398Z -->

```c
typedef struct ScsiPeripheral_BasicSenseInfo {...} ScsiPeripheral_BasicSenseInfo
```

## Overview

Defines the basic information about the sense data.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t responseCode | Response code.|
| bool valid | Information validity flag.|
| uint64_t information | **Information** field.|
| uint64_t commandSpecific | **Command-specific information** field.|
| bool sksv | Flag of the **Sense key specific** field.|
| uint32_t senseKeySpecific | **Sense key specific** field.|