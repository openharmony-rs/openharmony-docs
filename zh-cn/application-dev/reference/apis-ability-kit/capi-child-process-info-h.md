# child_process_info.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->

## 概述

定义子进程信息类型和访问器函数，用于从应用内子进程信息集合中按索引获取单个子进程信息句柄，并支持获取子进程的PID、父进程PID、进程名，以及释放子进程信息集合。

**引用文件：** <AbilityKit/ability_runtime/child_process_info.h>

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.1.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) | OH_AbilityRuntime_ChildProcessInfoHandle | 指向子进程信息的句柄。 |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md) | OH_AbilityRuntime_ChildProcessInfosHandle |  指向子进程信息集合的句柄。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)](#oh_abilityruntime_getchildprocessinfobyindex) | 按索引从子进程信息集合中获取特定子进程信息句柄。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)](#oh_abilityruntime_childprocessinfo_getpid) | 获取子进程的PID。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)](#oh_abilityruntime_childprocessinfo_getparentpid) | 获取子进程的父进程PID。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)](#oh_abilityruntime_childprocessinfo_getprocessname) | 获取子进程的进程名。 |
| [void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)](#oh_abilityruntime_releasechildprocessinfos) | 释放子进程信息集合。 |

## 函数说明

### OH_AbilityRuntime_GetChildProcessInfoByIndex()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)
```

**描述**

按索引从子进程信息集合中获取特定子进程信息句柄。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md) infos | 应用内所有子进程的信息集合。 |
| uint32_t index | 要获取的子进程信息的索引，必须严格小于子进程总数。 |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) *info | 输出对应索引处的单个子进程信息句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 接口调用成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 传入的参数无效。 |

### OH_AbilityRuntime_ChildProcessInfo_GetPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)
```

**描述**

获取子进程的PID。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) info | 子进程信息句柄，不能为空。 |
| int32_t *pid | 指向子进程PID的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 表示接口调用成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 传入的参数无效。 |

### OH_AbilityRuntime_ChildProcessInfo_GetParentPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)
```

**描述**

获取子进程的父进程PID。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) info | 子进程信息句柄，不能为空。 |
| int32_t *parentPid | 指向父进程PID的指针，不能为空。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 接口调用成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - 传入的参数无效。 |

### OH_AbilityRuntime_ChildProcessInfo_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)
```

**描述**

获取子进程的进程名。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) info | 子进程信息句柄，不能为空指针。 |
| char *processName | 用于接收进程名的缓冲区。 |
| uint32_t processNameSize | 缓冲区大小（字节），包含结尾的空字符。 |
| uint32_t *requiredSize | 实际所需大小（字节），包含结尾的空字符。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - 接口调用成功。<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - processName、info或requiredSize为空指针，或者processNameSize为0。<br>ABILITY_RUNTIME_ERROR_CODE_BUFFER_TOO_SMALL - 缓冲区过小。 |

### OH_AbilityRuntime_ReleaseChildProcessInfos()

```c
void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)
```

**描述**

释放子进程信息集合。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md) *infos | 待释放的子进程信息集合，不能为空。释放后句柄将被置为NULL。 |
