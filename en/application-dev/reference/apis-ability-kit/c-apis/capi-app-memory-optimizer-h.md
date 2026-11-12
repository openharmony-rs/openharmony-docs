# app_memory_optimizer.h

## Overview

Defines the child process active state type and notification function.

**File to Include**: <AbilityKit/ability_runtime/app_memory_optimizer.h>

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.1.0

**Related module**: [AbilityRuntime](capi-ability-kit-abilityruntime.md)

## Summary

### Enums

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AbilityRuntime_ChildProcessState](#oh_abilityruntime_childprocessstate) | OH_AbilityRuntime_ChildProcessState | Enumerates the active states of a child process.<br> A child process is in the active state by default when it is started. |

### Functions

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_NotifyChildProcessState(int32_t pid, OH_AbilityRuntime_ChildProcessState state)](#oh_abilityruntime_notifychildprocessstate) | Notifies the system of the active state of a child process of the current application.<br> When a child process is marked as inactive, the system can perform memory optimization on it. When the child process is marked as active again, the system stops performing memory optimization on it. Only the child processes created by the current application can be marked.<br> Only child processes created by the current application through system child process creation APIs can be marked. Processes forked by the application itself (such as by calling fork() directly or starting in SELF_FORK mode via childProcessManager.startChildProcess) are not supported; child processes created through other child process creation APIs (such as startArkChildProcess, startNativeChildProcess, and NDK APIs such as OH_Ability_StartNativeChildProcess) are supported.<br> This API can only be called in the main process of the application. If it is called in a child process, [ABILITY_RUNTIME_ERROR_CODE_CHILD_PROCESS_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.<br> This API is thread-safe and can be called from any thread. It is a synchronous call that blocks until the result is returned. Notifying the same state for the same child process repeatedly is idempotent: the call still succeeds and no additional state change callback is triggered. |

## Enum type description

### OH_AbilityRuntime_ChildProcessState

```c
enum OH_AbilityRuntime_ChildProcessState
```

**Description**

Enumerates the active states of a child process.<br> A child process is in the active state by default when it is started.

<!--Device-OH_AbilityRuntime_ChildProcessState--><!--Device-OH_AbilityRuntime_ChildProcessState-End-->

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.1.0

| Enum item | Description |
| -- | -- |
| OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_ACTIVE = 0 | The child process is active. The system does not perform memory optimization on it.<br>**Since**: 26.1.0 |
| OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_INACTIVE = 1 | The child process is inactive. The system can perform memory optimization on it.<br>**Since**: 26.1.0 |


## Function description

### OH_AbilityRuntime_NotifyChildProcessState()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_NotifyChildProcessState(int32_t pid, OH_AbilityRuntime_ChildProcessState state)
```

**Description**

Notifies the system of the active state of a child process of the current application.<br> When a child process is marked as inactive, the system can perform memory optimization on it. When the child process is marked as active again, the system stops performing memory optimization on it. Only the child processes created by the current application can be marked.<br> Only child processes created by the current application through system child process creation APIs can be marked. Processes forked by the application itself (such as by calling fork() directly or starting in SELF_FORK mode via childProcessManager.startChildProcess) are not supported; child processes created through other child process creation APIs (such as startArkChildProcess, startNativeChildProcess, and NDK APIs such as OH_Ability_StartNativeChildProcess) are supported.<br> This API can only be called in the main process of the application. If it is called in a child process, [ABILITY_RUNTIME_ERROR_CODE_CHILD_PROCESS_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.<br> This API is thread-safe and can be called from any thread. It is a synchronous call that blocks until the result is returned. Notifying the same state for the same child process repeatedly is idempotent: the call still succeeds and no additional state change callback is triggered.

<!--Device-AbilityRuntime_ErrorCode OH_AbilityRuntime_NotifyChildProcessState(int32_t pid, OH_AbilityRuntime_ChildProcessState state)--><!--Device-AbilityRuntime_ErrorCode OH_AbilityRuntime_NotifyChildProcessState(int32_t pid, OH_AbilityRuntime_ChildProcessState state)-End-->

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.1.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| int32_t pid | [in] PID of the child process. The value is the PID returned by the child process creation API. |
| [OH_AbilityRuntime_ChildProcessState](capi-app-memory-optimizer-h.md#oh_abilityruntime_childprocessstate) state | [in] Active state of the child process to set. Only [OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_ACTIVE](capi-app-memory-optimizer-h.md#oh_abilityruntime_childprocessstate) and [OH_ABILITY_RUNTIME_CHILD_PROCESS_STATE_INACTIVE](capi-app-memory-optimizer-h.md#oh_abilityruntime_childprocessstate) are accepted; for any other value, [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | <ul> <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.</li> <li>[ABILITY_RUNTIME_ERROR_CODE_CHILD_PROCESS_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the child process does not exist or is not created by the current application, or the API is called in a child process.</li> </ul> |


