# native_ability_wrapper.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @wangzhen416-->
<!--Designer: @ccllee1-->
<!--Tester: @lixueqing513-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=1e2bfcc9b4f85d9126c23f626a7a73b4bb891227 translatedAt=2026-09-03T08:49:30.864Z pushedAt=2026-09-05T10:47:30.111Z -->

## Overview

Provides the NativeAbility data information APIs for obtaining the Ability instance ID, Ability name, and napi_env.

**File to include:** <AbilityKit/ability_runtime/native_ability_wrapper.h>

**Library:** libability_runtime.so

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 26.0.0

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-nativeabilitywrapper.md) | AbilityRuntime_NativeAbilityWrapper | Defines the structure type of NativeAbility data information. |

### Functions

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityInstanceId(const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, char* buffer, const int32_t bufferSize)](#oh_abilityruntime_getabilityinstanceid) | Obtains the Ability instance ID from the NativeAbility data information. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityName(const AbilityRuntime_NativeAbilityWrapper *nativeAbilityWrapper, char *buffer, const int32_t bufferSize, int32_t *writeLength)](#oh_abilityruntime_getabilityname) | Obtains the Ability name from the NativeAbility data information. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_GetEnv(const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, napi_env* env)](#oh_abilityruntime_getenv) | Obtains napi_env from the NativeAbility data information. |

## Function Description

### OH_AbilityRuntime_GetAbilityInstanceId()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityInstanceId(
    const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper,
    char* buffer,
    const int32_t bufferSize)
```

**Description**

Obtains the Ability instance ID from the NativeAbility data information.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| [AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-nativeabilitywrapper.md)* nativeAbilityWrapper | Pointer to the NativeAbility data information. |
| char* buffer | Pointer to the buffer that receives the instance ID string. The instance ID is in UUID format and is 37 bytes long. |
| int32_t bufferSize | Length of the buffer, which must be at least 37 bytes. Ensure that the buffer has at least one extra byte for '\0'. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if nativeAbilityWrapper or buffer is a null pointer, or bufferSize is less than 37. |

**Example:**

```cpp
#include <AbilityKit/ability_runtime/native_ability_wrapper.h>
#include <AbilityKit/ability_runtime/ability_runtime_common.h>

void GetAbilityInstanceId(const AbilityRuntime_NativeAbilityWrapper* wrapper)
{
    if (wrapper == nullptr) {
        // Record the error log and perform other business processing.
        return;
    }
    // The buffer stores the Ability instance ID in UUID format.
    char buffer[37] = {0};
    // Obtain the Ability instance ID.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetAbilityInstanceId(wrapper, buffer, 37);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
        return;
    }
}
```

### OH_AbilityRuntime_GetAbilityName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetAbilityName(
    const AbilityRuntime_NativeAbilityWrapper *nativeAbilityWrapper, 
    char *buffer, 
    const int32_t bufferSize,
    int32_t *writeLength)
```

**Description**

Obtains the ability name from the NativeAbility data information.

**Since:** 26.0.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-nativeabilitywrapper.md)* nativeAbilityWrapper | Pointer to the NativeAbility data information. |
| char* buffer | Pointer to the buffer that receives the Ability name string. Pass nullptr to query the length of the Ability name. |
| int32_t bufferSize | Buffer length (in bytes). Ensure that the buffer has at least one extra byte for '\0'. |
| int32_t* writeLength | Length of the Ability name string to output. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if nativeAbilityWrapper or writeLength is a null pointer, or the buffer is too small to store the Ability name.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_ABILITY_WRAPPER_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the NativeAbility data information is invalid or incomplete.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs. |

**Example:**

```cpp
#include <AbilityKit/ability_runtime/native_ability_wrapper.h>
#include <AbilityKit/ability_runtime/ability_runtime_common.h>

void GetAbilityName(const AbilityRuntime_NativeAbilityWrapper* wrapper)
{
    if (wrapper == nullptr) {
        // Record the error log and perform other business processing.
        return;
    }

    const int32_t bufferSize = 256; // Adjust the buffer size as needed.
    char buffer[bufferSize] = {0};
    int32_t writeLength = 0;
    // Obtain the Ability name.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetAbilityName(wrapper, buffer, bufferSize, &writeLength);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other business processing.
        return;
    }
}
```

### OH_AbilityRuntime_GetEnv()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_GetEnv(
    const AbilityRuntime_NativeAbilityWrapper* nativeAbilityWrapper, 
    napi_env* env)
```

**Description**

Obtains the napi_env from the NativeAbility data information.

**Since:** 26.0.0

**Parameters**

| Parameter item | Description |
| -- | -- |
| [AbilityRuntime_NativeAbilityWrapper](capi-abilityruntime-nativeabilitywrapper.md)* nativeAbilityWrapper | Pointer to the NativeAbility data information. |
| napi_env* env | Pointer to receive the napi_env value. The napi_env remains valid until the process is terminated. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if nativeAbilityWrapper or env is a null pointer.<br>Returns [ABILITY_RUNTIME_ERROR_CODE_ABILITY_WRAPPER_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the NativeAbility data information is invalid or incomplete. |

**Example:**

```cpp
#include <AbilityKit/ability_runtime/native_ability_wrapper.h>
#include <AbilityKit/ability_runtime/ability_runtime_common.h>
#include <napi/native_api.h>

void GetEnv(const AbilityRuntime_NativeAbilityWrapper* wrapper)
{
    if (wrapper == nullptr) {
        // Record the error log and perform other service processing.
        return;
    }

    napi_env env = nullptr;
    // Obtain napi_env.
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_GetEnv(wrapper, &env);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record the error log and perform other service processing.
        return;
    }
}
```