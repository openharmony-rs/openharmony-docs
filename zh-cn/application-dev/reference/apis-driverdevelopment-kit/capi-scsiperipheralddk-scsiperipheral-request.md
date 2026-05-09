# ScsiPeripheral_Request
<!--Kit: Driver Development Kit-->
<!--Subsystem: Driver-->
<!--Owner: @zgene94-->
<!--Designer: @w00373942-->
<!--Tester: @dong-dongzhen-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct ScsiPeripheral_Request {...} ScsiPeripheral_Request
```

## 概述

请求参数结构体。

**起始版本：** 18

**相关模块：** [ScsiPeripheralDDK](capi-scsiperipheralddk.md)

**所在头文件：** [scsi_peripheral_types.h](capi-scsi-peripheral-types-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint8_t commandDescriptorBlock[[SCSIPERIPHERAL_MAX_CMD_DESC_BLOCK_LEN](capi-scsi-peripheral-types-h.md#scsiperipheral_max_cmd_desc_block_len)] | 命令描述符块。 |
| uint8_t cdbLength | 命令描述符块的长度。 |
| int8_t dataTransferDirection | 数据传输方向：-1为无数据传输的命令，-2为从主机到设备的数据传输(写)，-3为从设备到主机的数据传输(读)，-4为双向数据传输。 |
| [ScsiPeripheral_DeviceMemMap](capi-scsiperipheralddk-scsiperipheral-devicememmap.md)* data | 数据传输的缓冲区。 |
| uint32_t timeout | 超时时间（单位：毫秒）。 |


