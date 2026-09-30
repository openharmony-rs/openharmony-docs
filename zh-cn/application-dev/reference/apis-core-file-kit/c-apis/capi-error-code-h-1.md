# error_code.h

## 概述

Declare the error codes of file management module.

**引用文件：** <filemanagement/fileio/error_code.h>

**库：** NA

**起始版本：** 12

**相关模块：** [FileIO](capi-fileio.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [FileManagement_ErrCode](#filemanagement_errcode) | FileManagement_ErrCode | error codes of file management |

## 枚举类型说明

### FileManagement_ErrCode

```c
enum FileManagement_ErrCode
```

**描述：**

error codes of file management

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| ERR_OK = 0 | 接口调用成功。<br>**起始版本：** 12 |
| ERR_PERMISSION_ERROR = 201 | 接口权限校验失败。<br>**起始版本：** 12 |
| ERR_INVALID_PARAMETER = 401 | 无效入参。<br>**起始版本：** 12 |
| ERR_DEVICE_NOT_SUPPORTED = 801 | 当前设备不支持此接口。<br>**起始版本：** 12 |
| ERR_EPERM = 13900001 | 操作不被允许。<br>**起始版本：** 12 |
| ERR_ENOENT = 13900002 | 不存在此文件或文件夹。<br>**起始版本：** 12 |
| ERR_ENOMEM = 13900011 | 内存溢出。<br>**起始版本：** 12 |
| ERR_UNKNOWN = 13900042 | 内部未知错误。<br>**起始版本：** 12 |


