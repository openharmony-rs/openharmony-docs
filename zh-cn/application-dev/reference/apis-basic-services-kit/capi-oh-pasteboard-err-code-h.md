# oh_pasteboard_err_code.h
<!--Kit: Basic Services Kit-->
<!--Subsystem: MiscServices-->
<!--Owner: @yangxiaodong41-->
<!--Designer: @guo867-->
<!--Tester: @maxiaorong2-->
<!--Adviser: @HelloCrease-->

## 概述

声明剪贴板框架错误码信息。

**引用文件：** <database/pasteboard/oh_pasteboard_err_code.h>

**库：** libpasteboard.so

**系统能力：** SystemCapability.MiscServices.Pasteboard

**起始版本：** 13

**相关模块：** [Pasteboard](capi-pasteboard.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [PASTEBOARD_ErrCode](#pasteboard_errcode) | PASTEBOARD_ErrCode | 错误码信息。 |

## 枚举类型说明

### PASTEBOARD_ErrCode

```
enum PASTEBOARD_ErrCode
```

**描述：**

错误码信息。

**起始版本：** 13

| 枚举项 | 描述 |
| -- | -- |
| ERR_OK = 0 | 执行成功。 |
| ERR_PERMISSION_ERROR = 201 | 权限校验失败。 |
| ERR_INVALID_PARAMETER = 401 | 非法参数。 |
| ERR_DEVICE_NOT_SUPPORTED = 801 | 设备能力不支持。 |
| ERR_INNER_ERROR = 12900000 | 内部错误。 |
| ERR_BUSY = 12900003 | 系统忙。 |
| ERR_PASTEBOARD_COPY_FILE_ERROR = 12900007 | 文件拷贝失败。 |
| ERR_PASTEBOARD_PROGRESS_START_ERROR = 12900008 | 拉起进度显示失败。 |
| ERR_PASTEBOARD_PROGRESS_ABNORMAL = 12900009 | 进度显示异常。 |
| ERR_PASTEBOARD_GET_DATA_FAILED = 12900010 | 获取剪贴数据失败。 |


