# OH_CloudDisk_SyncFolderEx

```c
typedef struct OH_CloudDisk_SyncFolderEx {...} OH_CloudDisk_SyncFolderEx
```

## 概述

定义带占位符支持的云盘同步文件夹。 必须将版本字段设置为有效的版本宏(例如{@link OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1})，然后才能传递结构到任何API。 运行时使用版本来确定字段有效；当指定低版本时，在较高版本中引入的字段将被忽略。

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 26.0.1

**相关模块：** [CloudDisk](capi-clouddisk.md)

**所在头文件：** [oh_cloud_disk_manager.h](capi-oh-cloud-disk-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| uint32_t version | 指示此结构体的版本。必须初始化为有效的版本宏，例如 {@link OH_CLOUD_DISK_SYNC_FOLDER_EX_VERSION_1}。<br>**起始版本：** 26.0.1 |
| CloudDisk_SyncFolderPath path | sync文件夹路径。<br>**起始版本：** 26.0.1 |
| [CloudDisk_SyncFolderState](capi-oh-cloud-disk-manager-h.md#clouddisk_syncfolderstate) state | 指示同步文件夹的状态。<br>**起始版本：** 26.0.1 |
| [CloudDisk_DisplayNameInfo](capi-clouddisk-clouddisk-displaynameinfo.md) displayNameInfo | 同步文件夹的displayName信息。<br>**起始版本：** 26.0.1 |
| bool isSupportPlaceHolder | 同步文件夹是否支持占位符。<br>**起始版本：** 26.0.1 |


