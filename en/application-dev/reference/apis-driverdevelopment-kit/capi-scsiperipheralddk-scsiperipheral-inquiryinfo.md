# ScsiPeripheral_InquiryInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @hu-zhiqiong-->
<!-- md-trans-meta sourceCommit=ab207ee3a06b8d11d3acab43cad98a7c15093d61 translatedAt=2026-11-10T01:09:52.963Z pushedAt=2026-11-10T01:44:49.009Z nl=1 -->

```c
typedef struct ScsiPeripheral_InquiryInfo {...} ScsiPeripheral_InquiryInfo
```

## Overview

SCSI INQUIRY data, used to store the query result of the INQUIRY command of a SCSI peripheral.

**Since**: 18

**Related module**: [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**Header file**: [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| uint8_t deviceType | Device type of the SCSI peripheral. For details about the specific type values, see the SCSI standard protocol. |
| char idVendor[[SCSIPERIPHERAL_VENDOR_ID_LEN](capi-scsi-peripheral-types-h.md#macros) + 1] | Vendor ID. |
| char idProduct[[SCSIPERIPHERAL_PRODUCT_ID_LEN](capi-scsi-peripheral-types-h.md#macros) + 1] | Product ID. |
| char revProduct[[SCSIPERIPHERAL_PRODUCT_REV_LEN](capi-scsi-peripheral-types-h.md#macros) + 1] | Product version. |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | Pointer to the device memory map, used to store the queried data. |


