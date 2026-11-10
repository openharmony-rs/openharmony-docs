# ScsiPeripheral_InquiryRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=b5aa01b6af5d19922ff7e85249d00c2a9af91e2a translatedAt=2026-11-10T01:09:59.384Z pushedAt=2026-11-10T01:45:02.682Z nl=1 -->

```c
typedef struct ScsiPeripheral_InquiryRequest {...} ScsiPeripheral_InquiryRequest
```

## Overview

Request structure for the **SCSI INQUIRY** command, typically used to query basic device information.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t pageCode | **Page code** field. Set this field if you want to obtain certain types of device information. When an **Inquiry** command with a specific page code is run, the device returns details related to the page code. If the page code is set to **0x00**, it indicates that the standard inquiry data rather than the data of specific pages is requested.|
| uint16_t allocationLength | Allocation length field, which specifies the buffer size prepared by the request initiator (usually the host) for the response data. Unit: Byte. |
| uint8_t control | Control field, which specifies the control information of the SCSI command. |
| uint8_t byte1 | First byte of the CDB (Command Descriptor Block). |
| uint32_t timeout | Timeout interval, in milliseconds. |


