# child_process_info.h

## 概述

Defines the child process info type and accessor functions.

**库：** libability_runtime.so

**系统能力：** SystemCapability.Ability.AbilityRuntime.Core

**起始版本：** 26.1.0

**相关模块：** [AbilityRuntime](capi-abilityruntime.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AbilityRuntime_ChildProcessInfos](capi-abilityruntime-oh-abilityruntime-childprocessinfos.md) | *OH_AbilityRuntime_ChildProcessInfosHandle | 定义OH_AbilityRuntime_ChildProcessInfos指针。 |
| [OH_AbilityRuntime_ChildProcessInfo](capi-abilityruntime-oh-abilityruntime-childprocessinfo.md) | *OH_AbilityRuntime_ChildProcessInfoHandle | 定义OH_AbilityRuntime_ChildProcessInfo指针。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)](#oh_abilityruntime_getchildprocessinfobyindex) | 按其索引从集合中检索特定子进程信息句柄。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)](#oh_abilityruntime_childprocessinfo_getpid) | 获取子进程信息的PID。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)](#oh_abilityruntime_childprocessinfo_getparentpid) | 获取子进程的父进程PID。 |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)](#oh_abilityruntime_childprocessinfo_getprocessname) | 获取子进程信息的进程名称。 |
| [void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)](#oh_abilityruntime_releasechildprocessinfos) | 发布子进程信息收集。 |

## 函数说明

### OH_AbilityRuntime_GetChildProcessInfoByIndex()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)
```

**描述：**

按其索引从集合中检索特定子进程信息句柄。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfosHandle infos | 关于自身应用程序中所有子进程的信息。 |
| uint32_t index | 要检索的子进程信息的索引。必须严格小于计数。 |
| OH_AbilityRuntime_ChildProcessInfoHandle *info | 检索到的指定索引的单个子进程信息句柄。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>  如果操作成功，则返回<li>{@link_RUNTIME_ERROR_CODE_NO_ERROR}。</li>  <li>{@link_RUNTIME_ERROR_CODE_PARAM_INVALID}如果提供的参数无效。</li>  </ul> |

### OH_AbilityRuntime_ChildProcessInfo_GetPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)
```

**描述：**

获取子进程信息的PID。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfoHandle info | 指向子进程信息的指针。不能是nullptr。 |
| int32_t *pid | 输出参数，返回子进程PID。不能是nullptr。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>  如果操作成功，则返回<li>{@link_RUNTIME_ERROR_CODE_NO_ERROR}。</li>  <li>{@link_RUNTIME_ERROR_CODE_PARAM_INVALID}如果提供的参数无效。</li>  </ul> |

### OH_AbilityRuntime_ChildProcessInfo_GetParentPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)
```

**描述：**

获取子进程的父进程PID。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfoHandle info | 指向子进程信息的指针。不能是nullptr。 |
| int32_t *parentPid | 输出参数，返回父进程PID。不能是nullptr。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>  如果操作成功，则返回<li>{@link_RUNTIME_ERROR_CODE_NO_ERROR}。</li>  <li>{@link_RUNTIME_ERROR_CODE_PARAM_INVALID}如果提供的参数无效。</li>  </ul> |

### OH_AbilityRuntime_ChildProcessInfo_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)
```

**描述：**

获取子进程信息的进程名称。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfoHandle info | 【in】指向子进程信息的指针。它不能为NULL。 |
| char *processName | 【out】表示接收进程名的缓冲区。 |
| uint32_t processNameSize | 【in】表示缓冲区的大小（以字节为单位），包括尾随NUL。 |
| uint32_t *requiredSize | 【out】所需的大小（以字节为单位），包括尾随NUL。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>  如果操作成功，则返回<li>{@link_RUNTIME_ERROR_CODE_NO_ERROR}。</li>  <li>{@link_RUNTIME_ERROR_CODE_PARAM_INVALID}如果processName或requireSize为NULL，则  或者processNameSize为0。</li>  <li>如果缓冲区太小，则会出现<li>{@link_RUNTIME_ERROR_CODE_BUFFER_TOO_SMALL}。</li>  <li>如果字符串拷贝操作失败，则会出现<li>{@link_RUNTIME_ERROR_CODE_INTERNAL}。</li>  </ul> |

### OH_AbilityRuntime_ReleaseChildProcessInfos()

```c
void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)
```

**描述：**

发布子进程信息收集。

**起始版本：** 26.1.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfosHandle *infos | 【in】要释放的子进程信息。它不能为NULL。释放后，handle将被设置为NULL。 |


