# ScsiPeripheral_InquiryInfo

```c
typedef struct ScsiPeripheral_InquiryInfo {...} ScsiPeripheral_InquiryInfo
```

## Overview

Defines the SCSI inquiry data.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t deviceType | Device type. |
| char idVendor[SCSIPERIPHERAL_VENDOR_ID_LEN + 1] | Vendor ID. |
| char idProduct[SCSIPERIPHERAL_PRODUCT_ID_LEN + 1] | Product ID. |
| char revProduct[SCSIPERIPHERAL_PRODUCT_REV_LEN + 1] | Product version. |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) *data | Inquiry data. |


