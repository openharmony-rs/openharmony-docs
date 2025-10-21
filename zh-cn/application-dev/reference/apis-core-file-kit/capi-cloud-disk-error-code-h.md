# cloud_disk_error_code.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @oh_create_jiawei-->
<!--Designer: @oh_create_jiawei-->
<!--Tester: @liuhonggang123-->
<!--Adviser: @foryourself-->

## 概述

提供云盘管理模块的错误码定义。

**引用文件：** <filemanagement/cloud_disk_manager/cloud_disk_error_code.h>

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

```
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
| CLOUD_DISK_SYNC_FOLDER_PATH_UNAUTHORIZED = 34400002 | 同步根路径未授权。 |
| CLOUD_DISK_IPC_FAILED = 34400003 | IPC连接失败。 |
| CLOUD_DISK_SYNC_FOLDER_LIMIT_EXCEEDED = 34400004 | 同步根路径数量超过允许的限制。 |
| CLOUD_DISK_CONFLICT_THIS_APP = 34400005 | 同步根路径和该应用现有的同步根路径发生冲突。 |
| CLOUD_DISK_CONFLICT_OTHER_APP = 34400006 | 同步根路径和其他应用现有的同步根路径发生冲突。 |
| CLOUD_DISK_REGISTER_SYNC_FOLDER_FAILED = 34400007 | 同步根路径注册失败。 |
| CLOUD_DISK_SYNC_FOLDER_NOT_REGISTERED = 34400008 | 同步根路径未注册。 |
| CLOUD_DISK_UNREGISTER_SYNC_FOLDER_FAILED = 34400009 | 同步根路径取消注册失败。 |
| CLOUD_DISK_SYNC_FOLDER_PATH_NOT_EXIST = 34400010 | 同步根路径不存在。 |
| CLOUD_DISK_LISTENER_NOT_REGISTERED = 34400011 | 变更的监听未注册。 |
| CLOUD_DISK_LISTENER_ALREADY_REGISTERED = 34400012 | 变更的监听已注册。 |
| CLOUD_DISK_INVALID_CHANGE_SEQUENCE = 34400013 | 无效的变更序列，建议进行全部查询。 |
| CLOUD_DISK_TRY_AGAIN = 34400014 | 临时失败，建议重试（如：底层io负载过大、内存不足等）。 |
| CLOUD_DISK_NOT_ALLOWED = 34400015 | 当前设备不允许执行此功能。 |


