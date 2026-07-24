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

| 枚举项 | 描述 | 处理建议 |
| -- | -- | -- |
| CLOUD_DISK_OK = 0 | 接口调用成功。 | 无需处理。 |
| CLOUD_DISK_PERMISSION_DENIED = 201 | 接口权限校验失败。 | 请检查应用是否已申请所需权限。 |
| CLOUD_DISK_NOT_SUPPORTED = 801 | 当前设备不支持此功能。 | 请检查设备是否支持云盘管理相关系统能力。 |
| CLOUD_DISK_INVALID_ARG = 34400001 | 输入参数无效。 | 请检查参数类型、取值范围和格式是否符合接口要求。 |
| CLOUD_DISK_SYNC_FOLDER_PATH_UNAUTHORIZED = 34400002 | 同步根路径未授权。同步根路径是指应用用于云同步的本地目录路径。 | 请检查同步根路径是否已获得授权。 |
| CLOUD_DISK_IPC_FAILED = 34400003 | IPC连接失败。 | 请检查系统服务状态，或稍后重试。 |
| CLOUD_DISK_SYNC_FOLDER_LIMIT_EXCEEDED = 34400004 | 同步根路径数量超过允许的限制。 | 请检查并调整同步根路径数量。 |
| CLOUD_DISK_CONFLICT_THIS_APP = 34400005 | 同步根路径和该应用现有的同步根路径发生冲突。 | 请检查同步根路径是否重复或存在包含关系，调整后重试。 |
| CLOUD_DISK_CONFLICT_OTHER_APP = 34400006 | 同步根路径和其他应用现有的同步根路径发生冲突。 | 请选择其他路径或检查是否需要协调其他应用的同步设置。 |
| CLOUD_DISK_REGISTER_SYNC_FOLDER_FAILED = 34400007 | 同步根路径注册失败。 | 请检查路径是否有效、是否已授权、是否超限，修正后重试。 |
| CLOUD_DISK_SYNC_FOLDER_NOT_REGISTERED = 34400008 | 同步根路径未注册。 | 请先注册同步根路径后再执行相关操作。 |
| CLOUD_DISK_UNREGISTER_SYNC_FOLDER_FAILED = 34400009 | 同步根路径取消注册失败。 | 请检查路径是否已注册、是否存在未完成的同步任务，处理后再试。 |
| CLOUD_DISK_SYNC_FOLDER_PATH_NOT_EXIST = 34400010 | 同步根路径不存在。 | 请检查路径是否正确，或先创建该路径。 |
| CLOUD_DISK_LISTENER_NOT_REGISTERED = 34400011 | 变更监听器未注册。 | 请先注册变更监听器后再执行相关操作。 |
| CLOUD_DISK_LISTENER_ALREADY_REGISTERED = 34400012 | 变更监听器已注册。 | 请勿重复注册同一变更监听器。 |
| CLOUD_DISK_INVALID_CHANGE_SEQUENCE = 34400013 | 变更序列号无效或已过期，建议重新查询所有变更记录。 | 请重新发起全量变更查询。 |
| CLOUD_DISK_TRY_AGAIN = 34400014 | 临时失败，建议重试（如：底层I/O负载过大、内存不足等）。 | 请稍后重试。 |
| CLOUD_DISK_NOT_ALLOWED = 34400015 | 当前设备不允许执行此功能。 | 请检查设备是否满足功能要求，如系统版本、硬件配置等。 |


