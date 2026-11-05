# ScsiPeripheral_InquiryRequest

```c
struct ScsiPeripheral_InquiryRequest {...}
```

## Overview

Defines the SCSI command (**INQUIRY**) request struct, which is usually used to query basic device information.

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-others-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t pageCode | Page code** field. Set this field if you want to obtain certain types of device information. When an **Inquiry*<br> command with a specific page code is run, the device returns details related to the page code. If the page code is set to **0x00**, it indicates that the standard inquiry data rather than the data of specific pages is requested. |
| uint16_t allocationLength | Allocation length** field used to specify the size of the buffer prepared by the request initiator (usually the host) for the response data, in bytes. |
| uint8_t control | Control** field, which specifies the control flags of a SCSI command, such as the priority and linked command. |
| uint8_t byte1 | First byte of the SCSI command descriptor block (CDB), which usually contains the operation code and operation group information. |
| uint32_t timeout | Timeout interval, in milliseconds. |


