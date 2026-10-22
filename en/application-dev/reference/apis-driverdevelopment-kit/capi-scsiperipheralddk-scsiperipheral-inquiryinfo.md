# ScsiPeripheral_InquiryInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->

```c
typedef struct ScsiPeripheral_InquiryInfo {...} ScsiPeripheral_InquiryInfo
```

## Overview

Defines the SCSI **INQUIRY** data, which is used to store the query result of the **INQUIRY** command of SCSI peripherals.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t deviceType | Device type of the SCSI peripheral. For details about the type values, see the SCSI protocol.|
| char idVendor[[SCSIPERIPHERAL_VENDOR_ID_LEN](capi-scsi-peripheral-types-h.md#macros) + 1] | Vendor ID.|
| char idProduct[[SCSIPERIPHERAL_PRODUCT_ID_LEN](capi-scsi-peripheral-types-h.md#macros) + 1] | Product ID.|
| char revProduct[[SCSIPERIPHERAL_PRODUCT_REV_LEN](capi-scsi-peripheral-types-h.md#macros) + 1] | Product version.|
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | Pointer to the device memory mapping, which is used to store the queried data.|
