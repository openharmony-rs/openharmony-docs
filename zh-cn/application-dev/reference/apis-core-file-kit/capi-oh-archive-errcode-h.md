# oh_archive_errcode.h
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @rl123567-->
<!--Designer: @selina_jiang; @RainbowLLL-->
<!--Tester: @zheng1368-->
<!--Adviser: @jinqiuheng-->

## 概述

提供压缩解压模块错误码的声明。

**引用文件：** <filemanagement/archive/oh_archive_errcode.h>

**库：** liboharchive.so

**系统能力：** SystemCapability.FileManagement.File.FileIO

**起始版本：** 26.0.0

**相关模块：** [Archive](capi-archive.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_Archive_ErrCode](#oh_archive_errcode) | OH_Archive_ErrCode | 压缩解压模块错误码。 |

## 枚举类型说明

### OH_Archive_ErrCode

```c
enum OH_Archive_ErrCode
```

**描述**

压缩解压模块错误码。

**起始版本：** 26.0.0

| 枚举项 | 描述 |
| -- | -- |
| OH_ARCHIVE_OK = 0 | 操作成功。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_PARAM_ERROR = 401 | 无效入参。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_UNKNOWN_ERROR = 13900100 | 未知错误。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_CANCEL_ERROR = 13900101 | 用户取消操作。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_UNSUPPORTED_ERROR = 13900102 | 不支持当前压缩算法。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_MEM_ERROR = 13900103 | 内存分配失败。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_OPEN_ERROR = 13900104 | 打开归档文件失败。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_WRITE_ERROR = 13900105 | 写操作失败。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_READ_ERROR = 13900106 | 读操作失败。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_STREAM_OUTPUT_ERROR = 13900107 | 流输出错误。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_INSUFFICIENT_OUTBUF_ERROR = 13900108 | 输出缓冲区空间不足。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_NO_SPACE_ERROR = 13900200 | 磁盘空间不足。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_PATH_NOT_EXIST_ERROR = 13900201 | 路径不存在。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_PATH_EXISTS_ERROR = 13900202 | 路径已存在。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_PATH_ACCESS_ERROR = 13900203 | 路径访问错误。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_NAME_TOO_LONG_ERROR = 13900204 | 文件名过长。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_FULL_PATH_TOO_LONG_ERROR = 13900205 | 完整路径过长。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_DATA_ERROR = 13900300 | 数据完整性错误。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_CRC_ERROR = 13900301 | CRC校验错误。<br>**起始版本：** 26.0.0 |
| OH_ARCHIVE_DEFLATE_ERROR = 13900302 | DEFLATE算法错误。<br>**起始版本：** 26.0.0 |


