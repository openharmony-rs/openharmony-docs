# ScsiPeripheral_CapacityInfo

```c
struct ScsiPeripheral_CapacityInfo {...}
```

## 概述

SCSI READ CAPACITY结构体。用于在开发SCSI设备驱动时获取设备的存储容量信息，支持进行分区管理、可用空间检查和存储资源分配等操作。

**系统能力：** SystemCapability.Driver.SCSI.Extension

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-others-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t lbAddress | 逻辑块地址，用于指定读取容量的起始逻辑块位置。取值为0时获取设备整体容量信息。 |
| uint32_t lbLength | 单个逻辑块长度（单位：Byte）。表示每个逻辑块的字节大小，通常为512、2048或4096等标准值，具体取决于设备类型和格式化方式。 |


