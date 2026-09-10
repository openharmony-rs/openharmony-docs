# child_process_info.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @SKY2001-->
<!--Designer: @jsjzju-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f0ca4679538114d37c428618ebeb98dcc5067c5b translatedAt=2026-09-03T08:40:38.227Z pushedAt=2026-09-05T10:47:30.093Z -->

## Overview

Defines the child process information types and accessor functions, which are used to obtain the handle to a single child process information by index from the child process information set in an application, and to obtain the PID, parent PID, and process name of a child process, as well as to release the child process information set.

**File to include:** <AbilityKit/ability_runtime/child_process_info.h>

**Library:** libability_runtime.so

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 26.1.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) | OH_AbilityRuntime_ChildProcessInfoHandle | Handle to the child process information. |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md) | OH_AbilityRuntime_ChildProcessInfosHandle | Handle to the child process information set. |

### Functions

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)](#oh_abilityruntime_getchildprocessinfobyindex) | Obtains the handle to a specific child process information by index from the child process information set. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)](#oh_abilityruntime_childprocessinfo_getpid) | Obtains the PID of a child process. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)](#oh_abilityruntime_childprocessinfo_getparentpid) | Obtains the parent PID of a child process. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)](#oh_abilityruntime_childprocessinfo_getprocessname) | Obtains the process name of a child process. |
| [void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)](#oh_abilityruntime_releasechildprocessinfos) | Releases the child process information set. |

## Function Description

### OH_AbilityRuntime_GetChildProcessInfoByIndex()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetChildProcessInfoByIndex(OH_AbilityRuntime_ChildProcessInfosHandle infos, uint32_t index, OH_AbilityRuntime_ChildProcessInfoHandle *info)
```

**Description**

Obtains a specific child process information handle from the child process information set by index.

**Since:** 26.1.0

**Parameters**

| Parameter Item | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md) infos | Child process information set of all child processes in the application. |
| uint32_t index | Index of the child process information to obtain, which must be strictly less than the total number of child processes. |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) *info | Pointer to the single child process information handle at the corresponding index. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: API call succeeded.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: invalid parameter. |

### OH_AbilityRuntime_ChildProcessInfo_GetPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *pid)
```

**Description**

Obtains the PID of a child process.

**Since:** 26.1.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) info | Child process information handle, which must not be null. |
| int32_t *pid | Pointer to the PID of a child process, which must not be null. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - API call succeeded.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - invalid parameter. |

### OH_AbilityRuntime_ChildProcessInfo_GetParentPid()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetParentPid(OH_AbilityRuntime_ChildProcessInfoHandle info, int32_t *parentPid)
```

**Description**

Obtains the PID of the parent process of a child process.

**Since:** 26.1.0

**Parameters**

| Parameter Item | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) info | Child process information handle, which must not be null. |
| int32_t *parentPid | Pointer to the parent process PID, which must not be null. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - API call succeeded.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - invalid parameter. |

### OH_AbilityRuntime_ChildProcessInfo_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ChildProcessInfo_GetProcessName(OH_AbilityRuntime_ChildProcessInfoHandle info, char *processName, uint32_t processNameSize, uint32_t *requiredSize)
```

**Description**

Obtains the process name of a child process.

**Since:** 26.1.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfoHandle](capi-nativechildprocess-info.md) info | Child process information handle, which must not be a null pointer. |
| char *processName | Buffer used to receive the process name. |
| uint32_t processNameSize | Buffer size in bytes, including the terminating null character. |
| uint32_t *requiredSize | Actual required size in bytes, including the terminating null character. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - API call succeeded.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - processName, info, or requiredSize is a null pointer, or processNameSize is 0.<br>ABILITY_RUNTIME_ERROR_CODE_BUFFER_TOO_SMALL - The buffer is too small. |

### OH_AbilityRuntime_ReleaseChildProcessInfos()

```c
void OH_AbilityRuntime_ReleaseChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle *infos)
```

**Description**

Releases the child process information set.

**Since:** 26.1.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md) *infos | Child process information set to release, which must not be null. After the release, the handle is set to NULL. |
