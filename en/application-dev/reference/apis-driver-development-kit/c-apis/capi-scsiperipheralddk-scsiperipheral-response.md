# ScsiPeripheral_Response

```c
typedef struct ScsiPeripheral_Response {...} ScsiPeripheral_Response
```

## Overview

Defines the SCSI response parameters, including the status, error diagnosis data, and transfer result. It is used to receive the response data from the SCSI device and determine whether the command is successful.

<!--Device-struct ScsiPeripheral_Response {...}--><!--Device-struct ScsiPeripheral_Response {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t senseData[SCSIPERIPHERAL_MAX_SENSE_DATA_LEN] | Sense data, which is the status, error, and diagnosis information returned by the SCSI device to the host.<br><!--Device-uint8_t senseData[SCSIPERIPHERAL_MAX_SENSE_DATA_LEN]--><!--Device-uint8_t senseData[SCSIPERIPHERAL_MAX_SENSE_DATA_LEN]-End--> |
| [ScsiPeripheral_Status](capi-scsi-peripheral-types-h.md#scsiperipheral_status) status | Status when the call is complete. The options include **SCSIPERIPHERAL_STATUS_GOOD** (normal) and **SCSIPERIPHERAL_STATUS_BUSY** (busy).<br><!--Device-ScsiPeripheral_Status status--><!--Device-ScsiPeripheral_Status status-End--> |
| uint8_t maskedStatus | In the SCSI generic driver, this field is used to store the masked SCSI status.<br><!--Device-uint8_t maskedStatus--><!--Device-uint8_t maskedStatus-End--> |
| uint8_t msgStatus | Message status, indicating the message result after the SCSI command is executed.<br><!--Device-uint8_t msgStatus--><!--Device-uint8_t msgStatus-End--> |
| uint8_t sbLenWr | Number of valid bytes actually written to the sense buffer, which is used to determine the length of valid data in the **senseData** array. If the value is **0**, there is no sense data.<br><!--Device-uint8_t sbLenWr--><!--Device-uint8_t sbLenWr-End--> |
| uint16_t hostStatus | Host adapter status, for example, success (0x00), connection failure (0x01), busy bus (0x02), or timeout (0x03).<br><!--Device-uint16_t hostStatus--><!--Device-uint16_t hostStatus-End--> |
| uint16_t driverStatus | Driver status, for example, success (0x00) or busy device or resource (0x01).<br><!--Device-uint16_t driverStatus--><!--Device-uint16_t driverStatus-End--> |
| int32_t resId | Length deviation of the actually transmitted data, that is, the number of bytes that are not transmitted.<br><!--Device-int32_t resId--><!--Device-int32_t resId-End--> |
| uint32_t duration | SCSI command execution duration, in ms.<br><!--Device-uint32_t duration--><!--Device-uint32_t duration-End--> |


