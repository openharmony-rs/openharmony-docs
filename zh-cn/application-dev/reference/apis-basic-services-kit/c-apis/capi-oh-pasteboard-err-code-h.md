# oh_pasteboard_err_code.h

## 概述

声明剪贴板框架错误码信息。剪贴板错误码用于标识剪贴板操作过程中的执行结果，开发者可通过错误码判断操作是否成功以及失败的具体原因。

**引用文件：** <database/pasteboard/oh_pasteboard_err_code.h>

**库：** libpasteboard.so

**系统能力：** SystemCapability.MiscServices.Pasteboard

**起始版本：** 13

**相关模块：** [Pasteboard](capi-basic-services-kit-pasteboard.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [PASTEBOARD_ErrCode](#pasteboard_errcode) | PASTEBOARD_ErrCode | 剪贴板错误码枚举，用于标识剪贴板操作的执行结果，开发者可通过错误码判断操作是否成功以及失败的具体原因。 |

## 枚举类型说明

### PASTEBOARD_ErrCode

```c
enum PASTEBOARD_ErrCode
```

**描述：**

剪贴板错误码枚举，用于标识剪贴板操作的执行结果，开发者可通过错误码判断操作是否成功以及失败的具体原因。

<!--Device-enum PASTEBOARD_ErrCode--><!--Device-enum PASTEBOARD_ErrCode-End-->

**系统能力：** SystemCapability.MiscServices.Pasteboard

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| ERR_OK = 0 | 执行成功。<br><!--Device-ERR_OK = 0--><!--Device-ERR_OK = 0-End--> |
| ERR_PERMISSION_ERROR = 201 | 权限校验失败。<br><!--Device-ERR_PERMISSION_ERROR = 201--><!--Device-ERR_PERMISSION_ERROR = 201-End--> |
| ERR_INVALID_PARAMETER = 401 | 非法参数。<br><!--Device-ERR_INVALID_PARAMETER = 401--><!--Device-ERR_INVALID_PARAMETER = 401-End--> |
| ERR_DEVICE_NOT_SUPPORTED = 801 | 设备能力不支持。<br><!--Device-ERR_DEVICE_NOT_SUPPORTED = 801--><!--Device-ERR_DEVICE_NOT_SUPPORTED = 801-End--> |
| ERR_INNER_ERROR = 12900000 | 内部错误。<br><!--Device-ERR_INNER_ERROR = 12900000--><!--Device-ERR_INNER_ERROR = 12900000-End--> |
| ERR_BUSY = 12900003 | 系统忙。<br><!--Device-ERR_BUSY = 12900003--><!--Device-ERR_BUSY = 12900003-End--> |
| ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007 | 文件拷贝失败。<br>**起始版本：** 15<br><!--Device-ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007--><!--Device-ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007-End--> |
| ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008 | 拉起进度显示失败。<br>**起始版本：** 15<br><!--Device-ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008--><!--Device-ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008-End--> |
| ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009 | 进度显示异常。<br>**起始版本：** 15<br><!--Device-ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009--><!--Device-ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009-End--> |
| ERR_PASTEBOARD_GET_DATA_FAILED = 12900010 | 获取剪贴板数据失败。<br>**起始版本：** 15<br><!--Device-ERR_PASTEBOARD_GET_DATA_FAILED = 12900010--><!--Device-ERR_PASTEBOARD_GET_DATA_FAILED = 12900010-End--> |


