# context.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangzhongkai-->
<!--Designer: @yangzhongkai-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## 概述

提供上下文数据结构[AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md)和相关接口用于获取当前上下文的应用文件路径、数据加密等级和进程名等信息。

**引用文件：** <AbilityKit/ability_runtime/context.h>

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 24

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md) | - | 定义AbilityRuntime_Context结构体类型。 |
| [AbilityRuntime_Context*](capi-abilityruntime-abilityruntime-context8h.md) | AbilityRuntime_ContextHandle | 定义指向AbilityRuntime_Context的指针。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCacheDir(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getcachedir) | 获取上下文的缓存目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetTempDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_gettempdir) | 获取上下文的临时文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getfilesdir) | 获取上下文的通用文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDatabaseDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getdatabasedir) | 获取上下文的数据库文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetPreferencesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getpreferencesdir) | 获取上下文的首选项文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetBundleCodeDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getbundlecodedir) | 获取上下文的安装文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDistributedFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getdistributedfilesdir) | 获取上下文的分布式文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetResourceDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getresourcedir) | 获取上下文的资源目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCloudFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getcloudfiledir) | 获取上下文的云文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode* areaMode)](#oh_abilityruntime_context_getareamode) | 获取上下文的数据加密等级。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_SetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode areaMode)](#oh_abilityruntime_context_setareamode) | 设置上下文的数据加密等级。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetLogFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getlogfiledir) | 获取上下文的日志文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetProcessName(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getprocessname) | 获取进程名称。 |

## 函数说明

### OH_AbilityRuntime_Context_GetCacheDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCacheDir(
    AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的缓存目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context |  要获取缓存目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的缓存目录。 |
| int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetTempDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetTempDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的临时文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取临时文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的临时文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于最小要求。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetFilesDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的通用文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取通用文件目录的上下文。|
| char* buffer | 指向缓冲区的指针，用于接收上下文的通用文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetDatabaseDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDatabaseDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的数据库文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取数据库文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的数据库文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetPreferencesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetPreferencesDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的首选项文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取首选项文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的首选项文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于最小要求。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetBundleCodeDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetBundleCodeDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的安装文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取安装文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的安装文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetDistributedFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDistributedFilesDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的分布式文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取分布式文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的分布式文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetResourceDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetResourceDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的资源目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取资源目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的资源目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于最小要求。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetCloudFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCloudFileDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的云文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取云文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的云文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetAreaMode(
    AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode* areaMode)
```

**描述**

获取上下文的数据加密等级。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取数据加密等级的上下文。 |
| [AbilityRuntime_AreaMode](capi-context-constant-h.md#abilityruntime_areamode)* areaMode | 指向接收数据加密等级的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参areaMode为空。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_SetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_SetAreaMode(
    AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode areaMode)
```

**描述**

设置上下文的数据加密等级。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要设置数据加密等级的上下文。 |
| [AbilityRuntime_AreaMode](capi-context-constant-h.md#abilityruntime_areamode) areaMode | 数据加密等级。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参areaMode为空。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetLogFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetLogFileDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取上下文的日志文件目录。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取日志文件目录的上下文。 |
| char* buffer | 指向缓冲区的指针，用于接收上下文的日志文件目录。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于最小要求。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |

### OH_AbilityRuntime_Context_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetProcessName(
    AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取进程名称。

**起始版本：** 24

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | 要获取进程名称的上下文。|
| char* buffer | 指向缓冲区的指针，用于接收进程名称。 |
| int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 操作成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或writeLength为空或context为空，或缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 上下文不存在。 |
