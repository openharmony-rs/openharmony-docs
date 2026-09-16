# OH_CloudDisk_SyncFolderEx
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

```c
typedef struct OH_CloudDisk_SyncFolderEx {...} OH_CloudDisk_SyncFolderEx
```

## 概述

同步根路径属性信息，包含同步根路径、同步状态、显示名称和是否支持占位符等信息。开发者可通过该结构体获取同步根路径的完整属性，用于云盘同步功能中的同步根路径管理。

**起始版本：** 26.1.0

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| version | 同步根版本信息，当前版本信息为[OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-clouddisk-clouddisk-syncfolderex.md#OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1) 。|
| CloudDisk_SyncFolderPath path | 同步根路径，用于指定云盘同步的根目录位置。 |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | 同步根路径状态，具体取值及含义参见[CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate)。 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | 同步根路径别名信息，用于设置同步根路径的显示名称，便于用户识别和管理。
| isSupportPlaceHolder | 同步根路径是否支持占位符。 |

### 宏定义

| 名称 | 描述 |
| -- | -- |
| OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1 1| 同步根路径属性中的版本信息。<br>**起始版本：** 26.1.0 |

