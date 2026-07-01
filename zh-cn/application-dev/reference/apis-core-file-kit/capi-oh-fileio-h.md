# oh_fileio.h

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

## 概述

fileio模块接口定义，提供获取文件存储位置的native接口，帮助应用根据文件存储位置选择合适的访问策略等。

**引用文件：** <filemanagement/fileio/oh_fileio.h>

**库：** libohfileio.so

**系统能力：** SystemCapability.FileManagement.File.FileIO

**起始版本：** 12

**相关模块：** [FileIO](capi-fileio.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [FileIO_FileLocation](#fileio_filelocation) | FileIO_FileLocation | 文件存储位置枚举值。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)](#oh_fileio_getfilelocation) | 获取文件存储位置。 |

## 枚举类型说明

### FileIO_FileLocation

```c
enum FileIO_FileLocation
```

**描述**

文件存储位置枚举值。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| LOCAL = 1 | 文件存储于本地。 |
| CLOUD = 2 | 文件存储于云侧。 |
| LOCAL_AND_CLOUD = 3 | 文件存储于本地及云侧。 |


## 函数说明

### OH_FileIO_GetFileLocation()

```c
FileManagement_ErrCode OH_FileIO_GetFileLocation(char *uri, int uriLength, FileIO_FileLocation *location)
```

**描述**

获取文件存储位置，调用成功后，会将文件的存储位置写入到输出参数location中。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char *uri | URI字符串的指针，用于指定需要查询存储位置的文件。 |
| int uriLength | URI字符串的长度，不包含字符串结束符'\0'，单位为Byte。取值范围为(0，4096]。 |
| [FileIO_FileLocation](capi-oh-fileio-h.md#fileio_filelocation) *location | 文件存储位置的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | 返回FileManagement模块错误码[FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode)。 |


