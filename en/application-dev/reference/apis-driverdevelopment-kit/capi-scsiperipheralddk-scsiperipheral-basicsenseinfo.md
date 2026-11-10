# ScsiPeripheral_BasicSenseInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=5bd79eab01cf38af26bab98453bcb9f96f6c3f3c translatedAt=2026-11-10T01:09:32.415Z pushedAt=2026-11-10T01:42:45.575Z nl=1 -->

```c
typedef struct ScsiPeripheral_BasicSenseInfo {...} ScsiPeripheral_BasicSenseInfo
```

## Overview

Basic information structure of SCSI Sense Data, used to encapsulate the sense activation returned after a SCSI command is executed. This structure contains the response code, status flags, and various information fields, and is used by the driver to obtain and analyze the error status and command execution result of a SCSI device.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t responseCode | Response code. It is automatically set by the driver layer when Sense Data is received. |
| bool valid | Valid flag. When it is true, the information and commandSpecific fields are valid; when it is false, these fields should be ignored. Check this flag before use to avoid reading invalid data. |
| uint64_t information | Information field. Its value follows the SCSI standard protocol. |
| uint64_t commandSpecific | Command-specific information field. Its value follows the SCSI standard protocol. |
| bool sksv | Flag of the sense key specific field. When it is true, the senseKeySpecific field is valid and contains sense key specific data; when it is false, the senseKeySpecific field should be ignored. Check this flag before use to avoid reading invalid data. |
| uint32_t senseKeySpecific | Sense key specific field. Its value follows the SCSI standard protocol. |


