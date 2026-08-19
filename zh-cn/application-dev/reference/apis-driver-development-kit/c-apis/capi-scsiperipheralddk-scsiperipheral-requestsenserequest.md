# ScsiPeripheral_RequestSenseRequest

```c
typedef struct ScsiPeripheral_RequestSenseRequest {...} ScsiPeripheral_RequestSenseRequest
```

## 概述

SCSI命令（REQUEST SENSE）的请求结构体，该命令通常用于获取设备的错误信息。

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t allocationLength | Allocation length字段，用于指定请求发起者（通常是主机）为响应数据准备的缓冲区大小。单位：字节。 |
| uint8_t control | Control字段，用于指定SCSI命令的控制标志，如优先级、链接命令等控制选项。 |
| uint8_t byte1 | SCSI命令描述符块（CDB）的第一个字节，通常包含操作码和操作组信息。 |
| uint32_t timeout | 超时时间（单位：毫秒）。 |


