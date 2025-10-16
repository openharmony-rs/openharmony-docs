# CloudDisk_ChangeData
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

## 概述

定义了同步根路径下单个文件变更事件的数据结构。该结构包含有关文件变更的详细信息，包括唯一ID、父目录的唯一ID、相对路径、变更类型、文件大小和时间戳。

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint64_t updateSequenceNumber{0} | 变更事件的更新序列号。每次文件更改时单调递增加1，用于增量变更查询。范围：[0, 2^64 - 1]。 |
| CloudDisk_FileIdInfo fileId | 全局唯一的文件ID。在文件的生命周期内保持不变。 |
| CloudDisk_FileIdInfo parentFileId | 文件或目录所属父目录的唯一ID。 |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) relativePathInfo | 同步根路径下的文件，相对于同步根路径的相对路径。 |
| [CloudDisk_OperationType](capi-oh-cloud-disk-manager-h.md#clouddisk_operationtype) operationType | 此文件的变更操作类型（如：创建、删除、移动等）。 |
| uint64_t size{0} | 文件大小，单位：Byte。 |
| uint64_t mtime{0} | 文件修改时间，单位：ms。 |
| uint64_t timeStamp{0} | 变更事件发生时间，单位：ms。 |


