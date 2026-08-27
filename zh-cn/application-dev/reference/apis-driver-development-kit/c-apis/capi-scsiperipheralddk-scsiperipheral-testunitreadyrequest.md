# ScsiPeripheral_TestUnitReadyRequest

```c
typedef struct ScsiPeripheral_TestUnitReadyRequest {...} ScsiPeripheral_TestUnitReadyRequest
```

## 概述

SCSI命令（TEST UNIT READY）的请求结构体，通常用于确认逻辑单元是否就绪（逻辑单元是SCSI设备中可独立寻址的I/O操作实体）。

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t control | Control字段，用于指定SCSI命令的控制信息。 |
| uint32_t timeout | 超时时间（单位：ms）。 |


