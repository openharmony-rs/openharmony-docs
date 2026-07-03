# CloudDisk_ResultList
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct CloudDisk_ResultList {...} CloudDisk_ResultList
```

## 概述

表示一个文件同步操作的结果。该结构体包含文件路径信息、操作结果（成功或失败）、同步状态或失败原因。适用于查询文件同步操作结果的场景，开发者可通过isSuccess判断操作是否成功，并根据syncState或errorReason获取详细状态或失败原因。

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [CloudDisk_PathInfo](capi-clouddisk-clouddisk-pathinfo.md) pathInfo | 文件的绝对路径信息。 |
| bool isSuccess{false} | 表示操作是否成功。true：表示操作成功；false：表示操作失败。默认值为false。 |
| [CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate) syncState | 文件的同步状态，具体取值及含义参见[CloudDisk_SyncState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncstate)。当isSuccess为true时才生效。 |
| [CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason) errorReason | 文件同步操作失败的原因，具体错误类型及含义参见[CloudDisk_ErrorReason](capi-oh-cloud-disk-manager-h.md#clouddisk_errorreason)。当isSuccess为false时才生效。 |


