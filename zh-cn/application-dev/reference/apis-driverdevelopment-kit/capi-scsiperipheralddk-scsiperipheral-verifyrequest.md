# ScsiPeripheral_VerifyRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @lixinsheng2-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

## 概述

SCSI命令（verify）的请求结构体。

**起始版本：** 18

**相关模块：** [SCSIPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t lbAddress | 起始逻辑块地址。 |
| uint16_t verificationLength | 连续校验逻辑块的个数。 |
| uint8_t control | Control字段，用于指定一些控制信息。 |
| uint8_t byte1 | CDB的第一个字节。 |
| uint8_t byte6 | CDB的第六个字节。 |
| uint32_t timeout | 超时时间(单位: 毫秒)。 |


