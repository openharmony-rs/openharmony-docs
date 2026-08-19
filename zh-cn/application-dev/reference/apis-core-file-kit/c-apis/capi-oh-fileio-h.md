# oh_fileio.h

## 概述

fileio模块接口定义，提供获取文件存储位置的native接口，帮助应用根据文件存储位置选择合适的访问策略等。

**引用文件：** <filemanagement/fileio/oh_fileio.h>

**库：** libohfileio.so

**系统能力：** SystemCapability.FileManagement.File.FileIO

**起始版本：** 12

**相关模块：** [FileIO](capi-fileio.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [ FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)](#oh_fileio_getfilelocation) | Obtains the location of a file. |

## 函数说明

### OH_FileIO_GetFileLocation()

```c
 FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)
```

**描述**

Obtains the location of a file.

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char *uri | 指向入参uri的指针。 |
| int uriLength | 入参uri字符串的长度。 |
| FileIO_FileLocation *location | 输出文件存储位置的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FileManagement_ErrCode | 返回FileManagement模块错误码           {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.           {@link ERR_ENOENT} 13900002 - No such file or directory.           {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |


