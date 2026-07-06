# ScsiPeripheral_InquiryInfo
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct ScsiPeripheral_InquiryInfo {...} ScsiPeripheral_InquiryInfo
```

## 概述

SCSI INQUIRY 数据。

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t deviceType | 设备类型。 |
| char idVendor[[SCSIPERIPHERAL_VENDOR_ID_LEN](capi-scsi-peripheral-types-h.md#scsiperipheral_vendor_id_len) + 1] | 制造商 ID。 |
| char idProduct[[SCSIPERIPHERAL_PRODUCT_ID_LEN](capi-scsi-peripheral-types-h.md#scsiperipheral_product_id_len) + 1] | 产品 ID。 |
| char revProduct[[SCSIPERIPHERAL_PRODUCT_REV_LEN](capi-scsi-peripheral-types-h.md#scsiperipheral_product_rev_len) + 1] | 产品版本。 |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | 所有的查询数据。 |


