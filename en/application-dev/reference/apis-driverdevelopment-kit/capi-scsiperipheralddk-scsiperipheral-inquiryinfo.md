# ScsiPeripheral_InquiryInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct ScsiPeripheral_InquiryInfo {...} ScsiPeripheral_InquiryInfo
```

## Overview

Defines the SCSI inquiry data.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t deviceType | Device type.|
| char idVendor[[SCSIPERIPHERAL_VENDOR_ID_LEN](capi-scsi-peripheral-types-h.md) + 1] | Vendor ID.|
| char idProduct[[SCSIPERIPHERAL_PRODUCT_ID_LEN](capi-scsi-peripheral-types-h.md) + 1] | Product ID.|
| char revProduct[[SCSIPERIPHERAL_PRODUCT_REV_LEN](capi-scsi-peripheral-types-h.md) + 1] | Product version.|
| ScsiPeripheral_DeviceMemMap* data | Inquiry data.|
