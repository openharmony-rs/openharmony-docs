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

带占位符的同步根路径属性信息，包含同步根路径、同步状态、显示名称和是否支持占位符等信息，用于云盘同步功能中的带占位符同步根路径管理。使用时必须将版本字段设置为有效的版本宏(例如[OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#宏定义))，然后才能传递结构到任何API。运行时使用版本来确定字段有效；当指定低版本时，在较高版本中引入的字段将被忽略。

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t version | 指示此结构体的版本。必须初始化为有效的版本宏，例如[OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1](capi-oh-cloud-disk-manager-h.md#宏定义)。<br>**起始版本：** 26.0.1 |
| CloudDisk_SyncFolderPath path | 同步根路径，用于指定带占位符的云盘同步根目录位置。<br>**起始版本：** 26.0.1 |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | 同步根路径状态。<br>**起始版本：** 26.0.1 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | 同步根路径别名信息，用于设置同步根路径的显示名称，便于用户识别和管理。<br>**起始版本：** 26.0.1 |
| bool isSupportPlaceHolder | 同步根是否支持占位符。<br>**起始版本：** 26.0.1 |
