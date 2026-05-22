# dlp_permission_api.h
<!--Kit: Data Protection Kit-->
<!--Subsystem: Security-->
<!--Owner: @winnieHuYu-->
<!--Designer: @QRF-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->

## 概述

声明用于跨设备文件的权限管理、加密存储、授权访问等能力的接口。

**库：** libohdlp_permission.so

**引用文件：** <DataProtectionKit/dlp_permission_api.h>

**系统能力：** SystemCapability.Security.DataLossPrevention

**权限：** 无

**起始版本：** 14

**相关模块：** [DlpPermissionApi](capi-dlppermissionapi.md)

## 汇总

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [DLP_ErrCode](#dlp_errcode) | DLP_ErrCode | DLP（Data Loss Prevention）错误码的枚举。 |
| [DLP_FileAccess](#dlp_fileaccess) | DLP_FileAccess | DLP文件授权类型的枚举。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)](#oh_dlp_getdlppermissioninfo) | 查询当前DLP沙箱的权限信息。 |
| [DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char **originalFileName)](#oh_dlp_getoriginalfilename) | 获取指定DLP文件名的原始文件名。 |
| [DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)](#oh_dlp_isinsandbox) | 查询当前应用是否运行在DLP沙箱环境。 |
| [DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo)](#oh_dlp_setsandboxappconfig) | 设置沙箱应用配置信息。 |
| [DLP_ErrCode OH_DLP_GetSandboxAppConfig(char **configInfo)](#oh_dlp_getsandboxappconfig) | 获取沙箱应用配置信息。 |
| [DLP_ErrCode OH_DLP_CleanSandboxAppConfig()](#oh_dlp_cleansandboxappconfig) | 清理沙箱应用配置信息。 |

## 枚举类型说明

### DLP_ErrCode

```c
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

```c
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

```c
DLP_ErrCode OH_DLP_GetDlpPermissionInfo(DLP_FileAccess *dlpFileAccess, uint32_t *flags)
```

**描述**

查询当前DLP沙箱的权限信息。调用成功后，通过dlpFileAccess参数返回用户的授权类型，通过flags参数返回详细的操作权限。

**起始版本：** 14

 **使用场景**：在DLP沙箱应用中判断当前用户对文件的访问权限级别

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| dlpFileAccess | [DLP_FileAccess](#dlp_fileaccess)* | 是 | 表示DLP文件针对用户的授权类型，返回值为DLP_FileAccess枚举值，包括NO_PERMISSION（无权限）、READ_ONLY（只读）、CONTENT_EDIT（编辑）、FULL_CONTROL（完全控制）。 |
| flags | uint32_t* | 是 | 输出参数，表示DLP文件的详细操作权限，取值为位掩码，支持通过按位或运算组合多个权限。支持的权限位：<br>0x00000000-表示无文件权限。<br>0x00000001-表示文件的查看权限。<br>0x00000002-表示文件的保存权限。<br>0x00000004-表示文件的另存为权限。<br>0x00000008-表示文件的编辑权限。<br>0x00000010-表示文件的截屏权限。<br>0x00000020-表示文件的共享屏幕权限。<br>0x00000040-表示文件的录屏权限。<br>0x00000080-表示文件的复制权限。<br>0x00000100-表示文件的打印权限。<br>0x00000200-表示文件的导出权限。<br>0x00000400-表示文件的修改文件权限。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 返回DLP错误码，表示操作结果。<br>可能原因及处理步骤请参见[DLP服务错误码](errorcode-dlp.md)<br> 0 - 操作成功。<br>         19100001 - 入参错误。<br>         19100006 - 非DLP沙箱应用。<br>         19100011 - 系统服务工作异常。<br>         19100012 - 内存申请失败。 |

### OH_DLP_GetOriginalFileName()

```c
DLP_ErrCode OH_DLP_GetOriginalFileName(const char *fileName, char **originalFileName)
```

**描述**

获取指定DLP文件名的原始文件名。DLP文件在加密后会在原文件名后添加.dlp后缀，该接口通过去除.dlp后缀获取原始文件名。调用成功后，通过originalFileName参数返回原始文件名。调用者需使用free()释放originalFileName指向的内存。

**起始版本：** 14

**使用场景**： 在文件管理应用中显示DLP文件的原始名称

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| fileName | const char* | 是 | 指定要查询的文件名，不能为空指针。取值原则：需为有效的DLP文件名，支持绝对路径和相对路径。传入空指针或无效文件名时返回19100001错误码。 |
| originalFileName | char** | 是 | DLP文件的原始文件名。用于接收查询到的原始文件名字符串，该字符串由系统分配内存，使用完毕后需要调用者调用free()函数释放内存。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 返回DLP错误码，表示操作结果。<br>可能原因及处理步骤请参见[DLP服务错误码](errorcode-dlp.md)<br> 0 - 操作成功。<br>        19100001 - 入参错误。<br>         19100012 - 内存申请失败。 |

### OH_DLP_IsInSandbox()

```c
DLP_ErrCode OH_DLP_IsInSandbox(bool *isInSandbox)
```

**描述**

查询当前应用是否运行在DLP沙箱环境。调用成功后，通过isInSandbox参数返回判断结果。

**起始版本：** 14

 **使用场景**： 应用启动时判断运行环境，决定是否启用DLP相关功能

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| isInSandbox | bool* | 是 | 输出参数，用于接收当前应用是否运行在DLP沙箱环境的结果。true表示当前应用运行在DLP沙箱环境，false表示当前应用未运行在DLP沙箱环境。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 返回DLP错误码，表示操作结果。<br>可能原因及处理步骤请参见[DLP服务错误码](errorcode-dlp.md)<br>0 - 操作成功。<br>         19100011 - 系统服务工作异常。<br>         19100012 - 内存申请失败。 |

### OH_DLP_SetSandboxAppConfig()

```c
DLP_ErrCode OH_DLP_SetSandboxAppConfig(const char *configInfo)
```

**描述**

设置沙箱应用配置信息。配置信息为JSON格式字符串，包含应用在DLP沙箱中的行为配置。调用成功后，沙箱应用的配置信息将被更新。配置信息的格式为"xxx:xxx"。该接口不能在DLP沙箱环境中调用。

**起始版本：** 14

**使用场景**：根据业务需求动态调整沙箱应用的行为策略

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| configInfo | const char * | 是 | 沙箱应用配置信息，传入JSON格式的配置字符串，不能为空指针，设置后应用将按照配置信息运行。传入空指针或无效配置时返回19100001错误码。长度范围[0, 4194304)字节，超出此范围抛出异常。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 返回DLP错误码，表示操作结果。<br>可能原因及处理步骤请参见[DLP服务错误码](errorcode-dlp.md)<br>0 - 操作成功。<br>         19100001 - 入参错误。<br>         19100007 - DLP沙箱应用不允许调用此接口。<br>         19100011 - 系统服务工作异常。<br>         19100018 - 应用未授权。 |

### OH_DLP_GetSandboxAppConfig()

```c
DLP_ErrCode OH_DLP_GetSandboxAppConfig(char **configInfo)
```

**描述**

用于返回沙箱应用配置信息。 调用成功后，返回的配置信息为JSON格式字符串。该JSON格式字符串包含应用在DLP沙箱中的配置信息，调用者需使用free()释放内存。DLP沙箱是DLP技术为受保护文件创建的安全隔离环境，应用在打开DLP保护的文件时会自动运行在DLP沙箱中。该接口仅能在DLP沙箱环境中调用。

**起始版本：** 14

**使用场景**：在功能执行前检查配置是否满足要求

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| -- | -- | -- | -- |
| configInfo | char** | 是 | 输出参数，返回沙箱应用配置信息，为JSON格式字符串。该字符串由系统分配内存，使用完毕后需要调用者调用free()函数释放内存。|

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 返回DLP错误码，表示操作结果。<br>可能原因及处理步骤请参见[DLP服务错误码](errorcode-dlp.md)<br>0 - 操作成功。<br>         19100011 - 系统服务工作异常。<br>         19100012 - 内存申请失败。<br>         19100018 - 应用未授权。 |

### OH_DLP_CleanSandboxAppConfig()

```c
DLP_ErrCode OH_DLP_CleanSandboxAppConfig()
```

**描述**

清理沙箱应用配置信息。调用成功后，沙箱应用将使用默认配置运行。该接口不能在DLP沙箱环境中调用。

**起始版本：** 14

 **使用场景**： 需要重置沙箱应用状态时清除所有配置

**返回：**

| 类型 | 说明 |
| -- | -- |
| [DLP_ErrCode](#dlp_errcode) | 返回DLP错误码，表示操作结果。<br>可能原因及处理步骤请参见[DLP服务错误码](errorcode-dlp.md)<br> 0 - 操作成功。<br>         19100007 - DLP沙箱应用不允许调用此接口。<br>         19100011 - 系统服务工作异常。<br>         19100018 - 应用未授权。 |


