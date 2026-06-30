# oh_environment.h

<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @wangke25; @gsl_1234; @wuchengjun5-->
<!--Designer: @gsl_1234; @wangke25-->
<!--Tester: @liuhonggang123; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->

## 概述

environment模块接口定义，使用environment提供的native接口，获取公共文件根目录的沙箱路径。

**引用文件：** <filemanagement/environment/oh_environment.h>

**库：** libohenvironment.so

**系统能力：** SystemCapability.FileManagement.File.Environment.FolderObtain

**设备行为差异**：
- API版本26.0.0+：该接口在2in1和tablet中可正常调用，在其他设备类型中返回801错误码。
- API版本11-24：该接口在2in1可正常调用，在其他设备类型中返回801错误码。

**起始版本：** 12

**相关模块：** [Environment](capi-environment.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)](#oh_environment_getuserdownloaddir) | 获取Download根目录沙箱路径。 |
| [FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)](#oh_environment_getuserdesktopdir) | 获取Desktop根目录沙箱路径。 |
| [FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)](#oh_environment_getuserdocumentdir) | 获取Document根目录沙箱路径。 |

## 函数说明

### OH_Environment_GetUserDownloadDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)
```

**描述**

获取当前用户下载目录的沙箱路径，用于访问对应目录中的文件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| char **result | 返回Download根目录的沙箱路径。该字符串由系统分配内存，调用者需在使用完毕后通过free()释放，避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | 返回FileManagement模块错误码[FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode)。 |

### OH_Environment_GetUserDesktopDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)
```

**描述**

获取当前用户桌面目录的沙箱路径，用于访问对应目录中的文件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| char **result | 返回Desktop根目录的沙箱路径。该字符串由系统分配内存，调用者需在使用完毕后通过free()释放，避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | 返回FileManagement模块错误码[FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode)。 |

### OH_Environment_GetUserDocumentDir()

```c
FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)
```

**描述**

获取当前用户文档目录的沙箱路径，用于访问对应目录中的文件。

**起始版本：** 12


**参数：**

| 参数项 | 描述 |
| -- | -- |
| char **result | 返回Document根目录的沙箱路径。该字符串由系统分配内存，调用者需在使用完毕后通过free()释放，避免内存泄漏。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode) | 返回FileManagement模块错误码[FileManagement_ErrCode](capi-error-code-h.md#filemanagement_errcode)。 |


