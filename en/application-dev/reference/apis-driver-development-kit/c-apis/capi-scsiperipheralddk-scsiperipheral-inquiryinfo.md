# ScsiPeripheral_InquiryInfo

```c
typedef struct ScsiPeripheral_InquiryInfo {...} ScsiPeripheral_InquiryInfo
```

## Overview

Defines the SCSI **INQUIRY** data, which is used to store the query result of the **INQUIRY** command of SCSI peripherals.

<!--Device-struct ScsiPeripheral_InquiryInfo {...}--><!--Device-struct ScsiPeripheral_InquiryInfo {...}-End-->

**System capability**: SystemCapability.Driver.SCSI.Extension

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint8_t deviceType | Device type of the SCSI peripheral. For details about the type values, see the SCSI protocol. |
| char idVendor[SCSIPERIPHERAL_VENDOR_ID_LEN + 1] | Vendor ID. |
| char idProduct[SCSIPERIPHERAL_PRODUCT_ID_LEN + 1] | Product ID. |
| char revProduct[SCSIPERIPHERAL_PRODUCT_REV_LEN + 1] | Product version. |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md) *data | Pointer to the device memory mapping, which is used to store the queried data. |


