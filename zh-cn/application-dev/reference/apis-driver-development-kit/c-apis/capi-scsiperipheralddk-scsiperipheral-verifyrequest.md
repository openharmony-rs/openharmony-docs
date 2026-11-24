# ScsiPeripheral_VerifyRequest

```c
typedef struct ScsiPeripheral_VerifyRequest {...} ScsiPeripheral_VerifyRequest
```

## 概述

SCSI命令（VERIFY）的请求结构体，该命令通常用于校验逻辑块的数据完整性。

<!--Device-struct ScsiPeripheral_VerifyRequest {...}--><!--Device-struct ScsiPeripheral_VerifyRequest {...}-End-->

**系统能力：** SystemCapability.Driver.SCSI.Extension

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-driver-development-kit-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t lbAddress | 起始逻辑块地址。<br><!--Device-uint32_t lbAddress--><!--Device-uint32_t lbAddress-End--> |
| uint16_t verificationLength | 要校验的连续逻辑块的数量。<br><!--Device-uint16_t verificationLength--><!--Device-uint16_t verificationLength-End--> |
| uint8_t control | Control字段，用于指定SCSI命令的控制信息。<br><!--Device-uint8_t control--><!--Device-uint8_t control-End--> |
| uint8_t byte1 | CDB（Command Descriptor Block，命令描述符块）的第一个字节。<br><!--Device-uint8_t byte1--><!--Device-uint8_t byte1-End--> |
| uint8_t byte6 | CDB（Command Descriptor Block，命令描述符块）的第六个字节。<br><!--Device-uint8_t byte6--><!--Device-uint8_t byte6-End--> |
| uint32_t timeout | 超时时间（单位：ms）。<br><!--Device-uint32_t timeout--><!--Device-uint32_t timeout-End--> |


