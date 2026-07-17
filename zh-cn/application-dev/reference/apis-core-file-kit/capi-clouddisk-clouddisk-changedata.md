# CloudDisk_ChangeData
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct CloudDisk_ChangeData {...} CloudDisk_ChangeData
```

## 概述

定义同步根路径下单个文件变更事件的数据结构。该结构体包含文件变更的详细信息，包括更新序列号、唯一ID、父目录的唯一ID、相对路径、变更类型、文件大小、文件修改时间和变更事件发生时间。适用于云盘文件同步、增量更新查询等场景。

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t updateSequenceNumber{0} | 变更事件的更新序列号。每次文件更改时单调递增加1，用于增量变更查询。范围：[0, 2^64 - 1]。建议记录上次查询的序列号，并在下次查询时从该序列号继续获取后续变更。 |
| CloudDisk_FileIdInfo fileId | 全局唯一的文件ID。在文件的生命周期内保持不变。 |
| CloudDisk_FileIdInfo parentFileId | 文件或目录所属父目录的唯一ID。 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | 文件相对于同步根路径的路径信息。 |
| [CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype) operationType | 此文件的变更操作类型，具体枚举值及其含义参见[CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype)。 |
| uint64_t size{0} | 文件大小，单位：Byte。 |
| uint64_t mtime{0} | 文件修改时间，单位：ms。 |
| uint64_t timeStamp{0} | 变更事件发生时间，单位：ms。 |


