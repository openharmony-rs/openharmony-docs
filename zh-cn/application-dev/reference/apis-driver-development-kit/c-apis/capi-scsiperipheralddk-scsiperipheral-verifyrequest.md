# ScsiPeripheral_VerifyRequest

```c
typedef struct ScsiPeripheral_VerifyRequest {...} ScsiPeripheral_VerifyRequest
```

## 概述

SCSI命令（VERIFY）的请求结构体，该命令通常用于校验逻辑块的数据完整性。

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t lbAddress | 逻辑块起始地址，用于指定SCSI外设读/写操作的起始逻辑块位置。 |
| uint16_t verificationLength | 要校验的连续逻辑块的数量。 |
| uint8_t control | Control字段，用于指定SCSI命令的控制标志，如优先级、链接命令等控制选项。 |
| uint8_t byte1 | SCSI命令描述符块（CDB）的第一个字节，通常包含操作码和操作组信息。 |
| uint8_t byte6 | SCSI命令描述符块（CDB）的第六个字节，根据命令类型包含不同的参数或标志信息。 |
| uint32_t timeout | 超时时间（单位：毫秒）。 |


