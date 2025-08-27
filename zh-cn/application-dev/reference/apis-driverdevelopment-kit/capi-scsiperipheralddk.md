# SCSIPeripheralDDK
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## 概述

SCSI Peripheral DDK是为开发者提供专门用于开发SCSI设备驱动程序的套件，提供了初始化DDK、释放DDK、打开关闭设备、读写设备等接口，并声明了SCSI Peripheral DDK API所需的宏、枚举变量和数据结构，用于在应用层进行SCSI设备驱动的开发。

**起始版本：** 18
## 文件汇总

| 名称 | 描述 |
| -- | -- |
| [scsi_peripheral_api.h](capi-scsi-peripheral-api-h.md) | 声明用于主机侧访问SCSI设备的SCSI Peripheral DDK接口。 |
| [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md) | 提供在SCSI Peripheral DDK（驱动开发工具包）API中使用的枚举变量、结构体和宏。 |
