# dlp_permission_api.h
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--SE: @lucky-jinduo-->
<!--TSE: @nacyli-->

## 概述

声明用于跨设备的文件的权限管理、加密存储、授权访问等能力的接口。

**库：** libohdlp_permission.so

**引用文件：** <DataProtectionKit/dlp_permission_api.h>

**系统能力：** SystemCapability.Security.DataLossPrevention

**起始版本：** 14

**相关模块：** [DlpPermissionApi](capi-dlppermissionapi.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [DLP_ErrCode](#dlp_errcode) | DLP_ErrCode | DLP错误码的枚举。 |
| [DLP_FileAccess](#dlp_fileaccess) | DLP_FileAccess | DLP文件授权类型的枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)](#oh_dlp_getdlppermissioninfo) | 查询当前DLP沙箱的权限信息。 |
| [DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char *originalFileName)](#oh_dlp_getoriginalfilename) | 获取指定DLP文件名的原始文件名。 |
| [DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)](#oh_dlp_isinsandbox) | 查询当前应用是否运行在DLP沙箱环境。 |
| [DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo)](#oh_dlp_setsandboxappconfig) | 设置沙箱应用配置信息。 |
| [DLP_ErrCode OH_DLP_GetSandboxAppConfig(char *configInfo)](#oh_dlp_getsandboxappconfig) | 获取沙箱应用配置信息。 |
| [DLP_ErrCode OH_DLP_CleanSandboxAppConfig()](#oh_dlp_cleansandboxappconfig) | 清理沙箱应用配置信息。 |

## 枚举类型说明

### DLP_ErrCode

```
enum DLP_ErrCode
```

**描述**

DLP错误码的枚举。

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| ERR_OH_SUCCESS = 0 | 表示操作成功。 |
| ERR_OH_INVALID_PARAMETER = 19100001 | 表示入参错误。 |
| ERR_OH_API_ONLY_FOR_SANDBOX = 19100006 | 表示非DLP沙箱应用。 |
| ERR_OH_API_NOT_FOR_SANDBOX = 19100007 | 表示DLP沙箱应用不允许调用此接口。 |
| ERR_OH_SYSTEM_SERVICE_EXCEPTION = 19100011 | 表示系统服务工作异常。 |
| ERR_OH_OUT_OF_MEMORY = 19100012 | 表示内存申请失败。 |
| ERR_OH_APPLICATION_NOT_AUTHORIZED = 19100018 | 表示应用未授权。 |

### DLP_FileAccess

```
enum DLP_FileAccess
```

**描述**

DLP文件授权类型的枚举。

**起始版本：** 14

| 枚举项 | 描述 |
| -- | -- |
| NO_PERMISSION = 0 | 表示无文件权限。 |
| READ_ONLY = 1 | 表示文件的只读权限。 |
| CONTENT_EDIT = 2 | 表示文件的编辑权限。 |
| FULL_CONTROL = 3 | 表示文件的完全控制权限。 |


## 函数说明

### OH_DLP_GetDlpPermissionInfo()

```
DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)
```

**描述**

查询当前DLP沙箱的权限信息。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| [DLP_FileAccess](#dlp_fileaccess) *dlpFileAccess | 表示DLP文件针对用户的授权类型，例如：只读。 |
| uint32_t *flags | 表示DLP文件的详细操作权限，操作权限的具体含义为：<br>0x00000000-表示无文件权限。<br>0x00000001-表示文件的查看权限。<br>0x00000002-表示文件的保存权限。<br>0x00000004-表示文件的另存为权限。<br>0x00000008-表示文件的编辑权限。<br>0x00000010-表示文件的截屏权限。<br>0x00000020-表示文件的共享屏幕权限。<br>0x00000040-表示文件的录屏权限。<br>0x00000080-表示文件的复制权限。<br>0x00000100-表示文件的打印权限。<br>0x00000200-表示文件的导出权限。<br>0x00000400-表示文件的修改文件权限。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 0 - 操作成功。<br>         19100001 - 入参错误。<br>         19100006 - 非DLP沙箱应用。<br>         19100011 - 系统服务工作异常。<br>         19100012 - 内存申请失败。 |

### OH_DLP_GetOriginalFileName()

```
DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char *originalFileName)
```

**描述**

获取指定DLP文件名的原始文件名。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *fileName | 指定要查询的文件名。 |
| char *originalFileName | DLP文件的原始文件名。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 0 - 操作成功。<br>         19100001 - 入参错误。<br>         19100012 - 内存申请失败。 |

### OH_DLP_IsInSandbox()

```
DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)
```

**描述**

查询当前应用是否运行在DLP沙箱环境。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| bool *isInSandbox | 当前应用是否运行在DLP沙箱环境。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 0 - 操作成功。<br>         19100011 - 系统服务工作异常。<br>         19100012 - 内存申请失败。 |

### OH_DLP_SetSandboxAppConfig()

```
DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo)
```

**描述**

设置沙箱应用配置信息。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| const char *configInfo | 沙箱应用配置信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 0 - 操作成功。<br>         19100001 - 入参错误。<br>         19100007 - DLP沙箱应用不允许调用此接口。<br>         19100011 - 系统服务工作异常。<br>         19100018 - 应用未授权。 |

### OH_DLP_GetSandboxAppConfig()

```
DLP_ErrCode OH_DLP_GetSandboxAppConfig(char *configInfo)
```

**描述**

获取沙箱应用配置信息。

**起始版本：** 14


**参数：**

| 参数项 | 描述 |
| -- | -- |
| char *configInfo | 沙箱应用配置信息。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 0 - 操作成功。<br>         19100011 - 系统服务工作异常。<br>         19100012 - 内存申请失败。<br>         19100018 - 应用未授权。 |

### OH_DLP_CleanSandboxAppConfig()

```
DLP_ErrCode OH_DLP_CleanSandboxAppConfig()
```

**描述**

清理沙箱应用配置信息。

**起始版本：** 14

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 0 - 操作成功。<br>         19100007 - DLP沙箱应用不允许调用此接口。<br>         19100011 - 系统服务工作异常。<br>         19100018 - 应用未授权。 |


