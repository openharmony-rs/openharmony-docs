# ScsiPeripheral_Response
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:10:26.867Z pushedAt=2026-11-10T01:46:16.661Z nl=1 -->

```c
typedef struct ScsiPeripheral_Response {...} ScsiPeripheral_Response
```

## Overview

Defines the SCSI response parameter struct, which contains the status, error diagnostic data, and transfer result, and is used to receive SCSI device response data and determine whether a command succeeds.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t senseData[[SCSIPERIPHERAL_MAX_SENSE_DATA_LEN](capi-scsi-peripheral-types-h.md#macros)] | Sense Data, which contains the status, error, and diagnostic information returned by the SCSI device to the host. |
| [ScsiPeripheral_Status](capi-scsi-peripheral-types-h.md#scsiperipheral_status) status | Status when the call is complete. Possible values include SCSIPERIPHERAL_STATUS_GOOD (normal status) and SCSIPERIPHERAL_STATUS_BUSY (busy). |
| uint8_t maskedStatus | In the SCSI generic driver, this field stores the SCSI status after mask processing. |
| uint8_t msgStatus | Message status, which indicates the message result after the SCSI command is executed. |
| uint8_t sbLenWr | Number of valid bytes actually written to the Sense Buffer, used to determine the length of valid data in the senseData array. A value of 0 indicates that there is no Sense Data. |
| uint16_t hostStatus | Host adapter status. For example: success (0x00), unable to connect (0x01), bus busy (0x02), and timeout (0x03). |
| uint16_t driverStatus | Driver status. For example: success (0x00) and device or resource busy (0x01). |
| int32_t resId | Length deviation of the actually transmitted data, that is, the number of bytes that are not transmitted.|
| uint32_t duration | Time consumed to execute the SCSI command (in ms). |


