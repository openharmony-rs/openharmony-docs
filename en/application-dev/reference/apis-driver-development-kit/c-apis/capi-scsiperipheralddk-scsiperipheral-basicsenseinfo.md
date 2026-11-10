# ScsiPeripheral_BasicSenseInfo

```c
struct ScsiPeripheral_BasicSenseInfo {...}
```

## Overview

Defines the basic information struct of SCSI sense data, which is used to encapsulate the sense data returned after a SCSI command is executed. This struct contains the response code, status flag, and various information fields, which are used by the driver to obtain and analyze the error status and command execution result of the SCSI device.

<!--Device-struct ScsiPeripheral_BasicSenseInfo {...}--><!--Device-struct ScsiPeripheral_BasicSenseInfo {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t responseCode | Response code. It is automatically set by the driver layer when the sense data is received. |
| bool valid | Information validity flag. If the value is **true**, the **information** and **commandSpecific** fields are valid. If the value is **false**, these fields should be ignored. Before using this flag, check it to avoid reading invalid data. |
| uint64_t information | information** field. The value must comply with the SCSI protocol. |
| uint64_t commandSpecific | commandSpecific** field. The value must comply with the SCSI protocol. |
| bool sksv | Flag of the **senseKeySpecific** field. If the value is **true**, the **senseKeySpecific** field is valid and contains sense key specific data. If the value is **false**, the **senseKeySpecific** field should be ignored. Before using this flag, check it to avoid reading invalid data. |
| uint32_t senseKeySpecific | senseKeySpecific** field. The value must comply with the SCSI protocol. |


