# child_process_info.h

## Overview

Defines the child process info type and accessor functions.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ChildProcessInfos](capi-abilityruntime-oh-abilityruntime-childprocessinfos.md) | *OH_AbilityRuntime_ChildProcessInfosHandle | Defines the pointer to OH_AbilityRuntime_ChildProcessInfos. |
| [OH_AbilityRuntime_ChildProcessInfo](capi-abilityruntime-oh-abilityruntime-childprocessinfo.md) | *OH_AbilityRuntime_ChildProcessInfoHandle | Defines the pointer to OH_AbilityRuntime_ChildProcessInfo. |

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)](#oh_abilityruntime_getchildprocessinfobyindex) | Retrieves a specific child process info handle from the collection by its index. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)](#oh_abilityruntime_childprocessinfo_getpid) | Gets PID of child process info. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)](#oh_abilityruntime_childprocessinfo_getparentpid) | Gets parent PID of child process info. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)](#oh_abilityruntime_childprocessinfo_getprocessname) | Gets process name of child process info. |
| [void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)](#oh_abilityruntime_releasechildprocessinfos) | Releases child process info collection. |

## Function description

### OH_AbilityRuntime_GetChildProcessInfoByIndex()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)
```

**Description**

Retrieves a specific child process info handle from the collection by its index.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfosHandle infos | [in] Information about all child processes within the self application. |
| uint32_t index | [in]The index of the child process info to retrieve. Must be strictly less than the count. |
| OH_AbilityRuntime_ChildProcessInfoHandle *info | [out] The retrieved single child process info handle for the specified index. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the arguments provided are invalid.</li>       </ul> |

### OH_AbilityRuntime_ChildProcessInfo_GetPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)
```

**Description**

Gets PID of child process info.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfoHandle info | [in] Pointer to child process info. It must not be NULL. |
| int32_t *pid | [out] Pointer to child process PID. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the arguments provided are invalid.</li>       </ul> |

### OH_AbilityRuntime_ChildProcessInfo_GetParentPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)
```

**Description**

Gets parent PID of child process info.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfoHandle info | [in] Pointer to child process info. It must not be NULL. |
| int32_t *parentPid | [out] Pointer to parent process PID. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if the arguments provided are invalid.</li>       </ul> |

### OH_AbilityRuntime_ChildProcessInfo_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)
```

**Description**

Gets process name of child process info.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfoHandle info | [in] Pointer to child process info. It must not be NULL. |
| char *processName | [out] Indicates a buffer to receive process name. |
| uint32_t processNameSize | [in] Indicates size of buffer in bytes, including the trailing NUL. |
| uint32_t *requiredSize | [out] Required size in bytes, including the trailing NUL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>{@link ABILITY_RUNTIME_ERROR_CODE_NO_ERROR} if the operation is successful.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID} if processName or requiredSize is NULL,<br>     or processNameSize is 0.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_BUFFER_TOO_SMALL} if the buffer is too small.</li><br>     <li>{@link ABILITY_RUNTIME_ERROR_CODE_INTERNAL} if string copy operation failed.</li>       </ul> |

### OH_AbilityRuntime_ReleaseChildProcessInfos()

```c
void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)
```

**Description**

Releases child process info collection.

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfosHandle *infos | [in] The child process infos to be released. It must not be NULL. After release, handle will be set to NULL. |


