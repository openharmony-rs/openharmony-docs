# ScsiPeripheral_Response
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_Response {...} ScsiPeripheral_Response
```

## Overview

Defines the SCSI response parameters, including the status, error diagnosis data, and transfer result. It is used to receive the response data from the SCSI device and determine whether the command is successful.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t senseData[[SCSIPERIPHERAL_MAX_SENSE_DATA_LEN](capi-scsi-peripheral-types-h.md#macros)] | Sense data, which is the status, error, and diagnosis information returned by the SCSI device to the host.|
| [ScsiPeripheral_Status](capi-scsi-peripheral-types-h.md#scsiperipheral_status) status | Status when the call is complete. The options include **SCSIPERIPHERAL_STATUS_GOOD** (normal) and **SCSIPERIPHERAL_STATUS_BUSY** (busy).|
| uint8_t maskedStatus | In the SCSI generic driver, this field is used to store the masked SCSI status.|
| uint8_t msgStatus | Message status, indicating the message result after the SCSI command is executed.|
| uint8_t sbLenWr | Number of valid bytes actually written to the sense buffer, which is used to determine the length of valid data in the **senseData** array. If the value is **0**, there is no sense data.|
| uint16_t hostStatus | Host adapter status, for example, success (0x00), connection failure (0x01), busy bus (0x02), or timeout (0x03).|
| uint16_t driverStatus | Driver status, for example, success (0x00) or busy device or resource (0x01).|
| int32_t resId | Length deviation of the actually transmitted data, that is, the number of bytes that are not transmitted.|
| uint32_t duration | SCSI command execution duration, in ms.|
