# native_ability_wrapper.h

## Overview

Declares the native ability wrapper APIs.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-abilityruntime-nativeabilitywrapper.md) | AbilityRuntime_NativeAbilityWrapper | Defines the AbilityRuntime_NativeAbilityWrapper structure type. |

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityInstanceId(const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, char* buffer, const int32_t bufferSize)](#oh_abilityruntime_getabilityinstanceid) | Get ability instance ID from NativeAbilityWrapper. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityName(const AbilityRuntime_NativeAbilityWrapper *nativeAbilityWrapper, char *buffer, const int32_t bufferSize, int32_t *writeLength)](#oh_abilityruntime_getabilityname) | Get ability name from NativeAbilityWrapper. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetEnv(const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, napi_env* env)](#oh_abilityruntime_getenv) | Get napi_env from NativeAbilityWrapper. |

## Function description

### OH_AbilityRuntime_GetAbilityInstanceId()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityInstanceId(const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, char* buffer, const int32_t bufferSize)
```

**Description**

Get ability instance ID from NativeAbilityWrapper.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-abilityruntime-nativeabilitywrapper.md)* nativeAbilityWrapper | The native ability wrapper pointer. |
| char* buffer | A pointer to a buffer that receives the instance ID string which is UUID format, an amount of 37 bytes, 36 chars plus an ending '\0'. |
| const int32_t bufferSize | The length of the buffer, must be at least 37. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the nativeAbilityWrapper or buffer is null,          or the buffer size is less than 37. |

### OH_AbilityRuntime_GetAbilityName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityName(const AbilityRuntime_NativeAbilityWrapper *nativeAbilityWrapper, char *buffer, const int32_t bufferSize, int32_t *writeLength)
```

**Description**

Get ability name from NativeAbilityWrapper.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-abilityruntime-nativeabilitywrapper.md) *nativeAbilityWrapper | The native ability wrapper pointer. |
| char *buffer | A pointer to a buffer that receives the ability name. Pass nullptr to query the ability name length. |
| const int32_t bufferSize | The length of the buffer. Make sure the buffer has at least one more byte for '\0'. |
| int32_t *writeLength | Outputs the ability name string length. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the nativeAbilityWrapper or writeLength is null,          or the buffer is too small for the ability name.          [ABILITY_RUNTIME_ERROR_CODE_ABILITY_WRAPPER_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the native ability wrapper is invalid or          incomplete.          [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) inner error. |

### OH_AbilityRuntime_GetEnv()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetEnv(const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, napi_env* env)
```

**Description**

Get napi_env from NativeAbilityWrapper.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.0

**Parameters**:

| Parameter | Description |
| -- | -- |
| [const AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-abilityruntime-nativeabilitywrapper.md)* nativeAbilityWrapper | The native ability wrapper pointer. |
| napi_env* env | A pointer to the receive napi_env value. napi_env is valid until the process terminates. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the nativeAbilityWrapper or env is null.          [ABILITY_RUNTIME_ERROR_CODE_ABILITY_WRAPPER_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the native ability wrapper is invalid or          incomplete. |


