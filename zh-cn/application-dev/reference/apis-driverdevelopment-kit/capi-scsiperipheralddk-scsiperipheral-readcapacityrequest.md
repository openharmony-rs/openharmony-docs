# ScsiPeripheral_ReadCapacityRequest
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct ScsiPeripheral_ReadCapacityRequest {...} ScsiPeripheral_ReadCapacityRequest
```

## 概述

SCSI命令（READ CAPACITY）的请求结构体，用于发送读取存储容量的命令，可帮助获取设备的逻辑块大小和总块数。

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t lbAddress | 逻辑单元地址。 |
| uint8_t control | Control字段，用于指定SCSI命令的控制信息。 |
| uint8_t byte8 | CDB（Command Descriptor Block，命令描述块）的第八个字节。 |
| uint32_t timeout | 超时时间（单位: 毫秒）。 |


