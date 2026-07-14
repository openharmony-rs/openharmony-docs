# oh_environment.h

## 概述

Provide environment APIS.

**库：** libohenvironment.so

**系统能力：** SystemCapability.FileManagement.File.Environment.FolderObtain

**起始版本：** 12

**相关模块：** [Environment](capi-environment.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [ FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)](#oh_environment_getuserdownloaddir) | 获取Download根目录沙箱路径。 |
| [ FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)](#oh_environment_getuserdesktopdir) | 获取Desktop根目录沙箱路径。 |
| [ FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)](#oh_environment_getuserdocumentdir) | 获取Document根目录沙箱路径。 |

## 函数说明

### OH_Environment_GetUserDownloadDir()

```c
 FileManagement_ErrCode OH_Environment_GetUserDownloadDir(char **result)
```

**描述**

获取Download根目录沙箱路径。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char **result | Download根目录路径指针。请引用头文件malloc.h并使用free()进行资源释放。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FileManagement_ErrCode | 返回FileManagement模块错误码。<br>          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>          {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>          {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |

### OH_Environment_GetUserDesktopDir()

```c
 FileManagement_ErrCode OH_Environment_GetUserDesktopDir(char **result)
```

**描述**

获取Desktop根目录沙箱路径。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char **result | Desktop根目录路径指针。请引用头文件malloc.h并使用free()进行资源释放。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FileManagement_ErrCode | 返回FileManagement模块错误码。<br>          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>          {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>          {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |

### OH_Environment_GetUserDocumentDir()

```c
 FileManagement_ErrCode OH_Environment_GetUserDocumentDir(char **result)
```

**描述**

获取Document根目录沙箱路径。

**起始版本：** 12

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char **result | Document根目录路径指针。请引用头文件malloc.h并使用free()进行资源释放。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| FileManagement_ErrCode | 返回FileManagement模块错误码。<br>          {@link ERR_INVALID_PARAMETER} 401 - Invalid input parameter, pointer is null.<br>          {@link ERR_DEVICE_NOT_SUPPORTED} 801 - Device not supported.<br>          {@link ERR_ENOMEM} 13900011 - Failed to apply for memory. |


