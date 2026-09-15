# cloud_disk_error_code.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @jinqiuheng-->

## 概述

提供云盘管理模块的错误码定义，用于标识云盘管理接口调用过程中的异常情况，帮助开发者定位和处理权限校验失败、参数无效、路径冲突、IPC连接失败等问题。

**引用文件：** `<filemanagement/clouddiskmanager/cloud_disk_error_code.h>`

**库：** libohclouddiskmanager.so

**系统能力：** SystemCapability.FileManagement.CloudDiskManager

**起始版本：** 21

**相关模块：** [CloudDisk](capi-clouddisk.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [CloudDisk_ErrorCode](#clouddisk_errorcode) | CloudDisk_ErrorCode | 定义云盘管理模块的错误码。 |

## 枚举类型说明

### CloudDisk_ErrorCode

```c
enum CloudDisk_ErrorCode
```

**描述**

定义云盘管理模块的错误码。

**起始版本：** 21

| 枚举项 | 描述 |
| -- | -- |
| CLOUD_DISK_OK = 0 | 接口调用成功。 |
| CLOUD_DISK_PERMISSION_DENIED = 201 | 接口权限校验失败。 |
| CLOUD_DISK_NOT_SUPPORTED = 801 | 当前设备不支持此功能。 |
| CLOUD_DISK_INVALID_ARG = 34400001 | 输入参数无效。 |
| CLOUD_DISK_SYNC_FOLDER_PATH_UNAUTHORIZED = 34400002 | 同步根路径未授权。同步根路径是指应用用于云同步的本地目录路径。 |
| CLOUD_DISK_IPC_FAILED = 34400003 | IPC连接失败。 |
| CLOUD_DISK_SYNC_FOLDER_LIMIT_EXCEEDED = 34400004 | 同步根路径数量超过允许的限制。 |
| CLOUD_DISK_CONFLICT_THIS_APP = 34400005 | 同步根路径和该应用现有的同步根路径发生冲突。 |
| CLOUD_DISK_CONFLICT_OTHER_APP = 34400006 | 同步根路径和其他应用现有的同步根路径发生冲突。 |
| CLOUD_DISK_REGISTER_SYNC_FOLDER_FAILED = 34400007 | 同步根路径注册失败。 |
| CLOUD_DISK_SYNC_FOLDER_NOT_REGISTERED = 34400008 | 同步根路径未注册。 |
| CLOUD_DISK_UNREGISTER_SYNC_FOLDER_FAILED = 34400009 | 同步根路径取消注册失败。 |
| CLOUD_DISK_SYNC_FOLDER_PATH_NOT_EXIST = 34400010 | 同步根路径不存在。 |
| CLOUD_DISK_LISTENER_NOT_REGISTERED = 34400011 | 变更监听器未注册。 |
| CLOUD_DISK_LISTENER_ALREADY_REGISTERED = 34400012 | 变更监听器已注册。 |
| CLOUD_DISK_INVALID_CHANGE_SEQUENCE = 34400013 | 变更序列号无效或已过期，建议重新查询所有变更记录。 |
| CLOUD_DISK_TRY_AGAIN = 34400014 | 临时失败，建议重试（如：底层I/O负载过大、内存不足等）。 |
| CLOUD_DISK_NOT_ALLOWED = 34400015 | 当前设备不允许执行此功能。 |
| OH_CLOUD_DISK_FILE_ALREADY_EXISTS = 34400016 | 目标路径下已存在同名文件。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_NOT_A_PLACEHOLDER = 34400017 | 目标路径不是占位符文件。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_IS_A_PLACEHOLDER = 34400018 | 目标路径已经是占位符文件。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_HYDRATE_IN_PROGRESS = 34400019 | 占位符文件正在水合中。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_NO_SPACE_LEFT = 34400020 | 磁盘剩余空间不足。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_CALLBACK_NOT_REGISTERED = 34400021 | 回调表没有注册。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_CALLBACK_ALREADY_REGISTERED = 34400022 | 回调表已经注册。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_NOT_A_DIRECTORY = 34400023 | 目标路径的父目录不是目录。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_FILE_NOT_EXIST = 34400024 | 目标路径不存在。<br>**起始版本：** 26.1.0 |
| OH_CLOUD_DISK_NAME_TOO_LONG = 34400025 | 文件名或路径过长。<br>**起始版本：** 26.1.0 |
