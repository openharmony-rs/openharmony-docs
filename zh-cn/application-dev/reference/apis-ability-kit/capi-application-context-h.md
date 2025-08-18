# application_context.h

## 概述

提供应用级别上下文相关的接口。

**引用文件：** <AbilityKit/ability_runtime/application_context.h>

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 13

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCacheDir(char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcachedir) | 获取本应用的应用级的缓存目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetAreaMode(AbilityRuntime_AreaMode* areaMode)](#oh_abilityruntime_applicationcontextgetareamode) | 获取本应用的应用级的文件数据加密等级。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleName(char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlename) | 获取应用包名。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgettempdir) | 获取本应用的应用级的临时文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetfilesdir) | 获取本应用的应用级的通用文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdatabasedir) | 获取本应用的应用级的数据库文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetpreferencesdir) | 获取本应用的应用级的首选项文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlecodedir) | 获取本应用的应用级的安装文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdistributedfilesdir) | 获取本应用的应用级的分布式文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcloudfiledir) | 获取本应用的应用级的云文件目录。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetresourcedir) | 获取应用级别的资源目录。     |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)](#oh_abilityruntime_startselfuiability) | 启动当前应用的UIAbility。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want,AbilityRuntime_StartOptions *options)](#oh_abilityruntime_startselfuiabilitywithstartoptions) | 通过StartOptions启动当前应用的UIAbility。 |

## 函数说明

### OH_AbilityRuntime_ApplicationContextGetCacheDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCacheDir(char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的缓存目录。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收本应用的应用级的缓存目录。 |
| int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetAreaMode()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetAreaMode(AbilityRuntime_AreaMode* areaMode)
```

**描述**

获取本应用的应用级的文件数据加密等级。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityRuntime_AreaMode](capi-context-constant-h.md#abilityruntime_areamode)* areaMode | 指向接收数据加密等级的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetBundleName()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleName(char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取应用包名。

**起始版本：** 13

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetTempDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的临时文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetFilesDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的通用文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetDatabaseDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的数据库文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetPreferencesDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的首选项文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetBundleCodeDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的安装文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的分布式文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetCloudFileDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的云文件目录。

**起始版本：** 16

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| const int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_ApplicationContextGetResourceDir()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**描述**

获取本应用的应用级的资源目录。

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| char* moduleName | 模块名。 |
| char* buffer | 指向缓冲区的指针，用于接收应用包名。 |
| int32_t bufferSize | 缓冲区大小，单位为字节。 |
| int32_t* writeLength | 在返回[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode)时，表示实际写入到缓冲区的字符串长度，单位为字节。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | 返回执行结果。<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 查询成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 入参buffer或者writeLength为空，或者缓冲区大小小于需要写入的大小。<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - 应用上下文不存在，如在应用创建的[子进程](capi-childprocess.md)中应用级别上下文不存在。 |

### OH_AbilityRuntime_StartSelfUIAbility()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)
```

**描述**

启动当前应用的UIAbility。

> **说明：**
>
> 当前仅支持2in1设备。

**需要权限：** ohos.permission.NDK_START_SELF_UI_ABILITY

**起始版本：** 15

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityBase_Want](capi-abilitybase-want.md) *want | 启动当前应用UIAbility时需要的Want信息。 |

**返回：**
 
| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 接口调用成功。<br>ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED - 调用方权限校验失败。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 调用方入参校验失败。<br>ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED - 设备类型不支持。<br>ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY - 指定的Ability名称不存在。<br>ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE - 接口调用Ability类型错误。<br>ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED - 众测应用到期。<br>ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE - Wukong模式，不允许启动/停止Ability。<br>ABILITY_RUNTIME_ERROR_CODE_CONTROLLED - 应用被管控。<br>ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED - 应用被EDM管控。<br>ABILITY_RUNTIME_ERROR_CODE_CROSS_APP - 限制API 11以上版本三方应用跳转。<br>ABILITY_RUNTIME_ERROR_CODE_INTERNAL - 内部错误。<br>ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY - 非顶层应用。<br>ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED - 应用多实例已达到上限（从API17开始）。<br>ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED - 不允许设置APP_INSTANCE_KEY（从API17开始）。<br>详细内容参考AbilityRuntime_ErrorCode。 |

**示例代码：**

```cpp
#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>

void startSelfUIAbilityTest()
{
    AbilityBase_Element element;
    element.abilityName = const_cast<char*>("EntryAbility");
    element.bundleName = const_cast<char*>("com.example.myapplication");
    element.moduleName = const_cast<char*>("entry");
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);

    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_StartSelfUIAbility(want);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // 记录错误日志以及其他业务处理
        return;
    }
    // 销毁want，防止内存泄漏
    OH_AbilityBase_DestroyWant(want);
}
```

### OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions()

```
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want,AbilityRuntime_StartOptions *options)
```

**描述**

通过StartOptions启动当前应用的UIAbility。

> **说明：**
>
> 当前仅支持2in1设备。

**需要权限：** ohos.permission.NDK_START_SELF_UI_ABILITY

**起始版本：** 17

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [AbilityBase_Want](capi-abilitybase-want.md) *want | 启动当前应用UIAbility时需要的Want信息。 |
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *options | 启动当前应用UIAbility时需要的StartOptions信息。如果该参数中[startVisibility](capi-context-constant-h.md#abilityruntime_startvisibility)属性的值不为空，必须确保当前应用已添加到状态栏，否则会返回[ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode)错误码。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 接口调用成功。<br>ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED - 调用方权限校验失败。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 调用方入参校验失败。<br>ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED - 设备类型不支持。<br>ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY - 指定的Ability名称不存在。<br>ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE - 接口调用Ability类型错误。<br>ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED - 众测应用到期。<br>ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE - Wukong模式，不允许启动/停止Ability。<br>ABILITY_RUNTIME_ERROR_CODE_CONTROLLED - 应用被管控。<br>ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED - 应用被EDM管控。<br>ABILITY_RUNTIME_ERROR_CODE_CROSS_APP - 限制API 11以上版本三方应用跳转。<br>ABILITY_RUNTIME_ERROR_CODE_INTERNAL - 内部错误。<br>ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY - 非顶层应用。<br>ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED - 不允许设置窗口启动可见性。<br>ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED - 不支持应用分身和多实例。<br>ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY - 无效多实例。<br> ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED - 应用多实例以达到上限。<br>ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED - 不支持应用多实例。<br>ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED - 不允许设置APP_INSTANCE_KEY。<br>详细内容参考AbilityRuntime_ErrorCode。 |

**示例代码：**

```cpp
#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>

void demo()
{
    AbilityBase_Element element;
    element.abilityName = const_cast<char*>("EntryAbility");
    element.bundleName = const_cast<char*>("com.example.myapplication");
    element.moduleName = const_cast<char*>("entry");
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);
    if (want == nullptr) {
        // 记录错误日志以及其他业务处理
        return;
    }

    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // 记录错误日志以及其他业务处理

        // 销毁want，防止内存泄漏
        OH_AbilityBase_DestroyWant(want);
        return;
    }
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(want, options);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // 记录错误日志以及其他业务处理
    }
    // 销毁want，防止内存泄漏
    OH_AbilityBase_DestroyWant(want);

    // 销毁options，防止内存泄漏
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```
