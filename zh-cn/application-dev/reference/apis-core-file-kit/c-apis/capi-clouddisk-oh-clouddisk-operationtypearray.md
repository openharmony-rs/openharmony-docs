# OH_CloudDisk_OperationTypeArray

```c
typedef struct OH_CloudDisk_OperationTypeArray {...} OH_CloudDisk_OperationTypeArray
```

## 概述

存放文件变更类型枚举的数组。

<!--Device-struct OH_CloudDisk_OperationTypeArray {...}--><!--Device-struct OH_CloudDisk_OperationTypeArray {...}-End-->

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.1.0

**相关模块：** [CloudDisk](capi-core-file-kit-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [const CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype) *data | 指向元素类型为[CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype)数组的指针。<br>**起始版本：** 26.1.0<br><!--Device-const CloudDisk_OperationType *data--><!--Device-const CloudDisk_OperationType *data-End--> |
| int64_t length | 数组的长度，范围是[1, 8]。<br>**起始版本：** 26.1.0<br><!--Device-int64_t length--><!--Device-int64_t length-End--> |


