# context.h

## Overview

Declare the common types for the context AbilityRuntime.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md) | - | Define the AbilityRuntime_Context structure type. |
| [AbilityRuntime_Context*](capi-abilityruntime-abilityruntime-context8h.md) | AbilityRuntime_ContextHandle | Defines the pointer to AbilityRuntime_Context. |

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCacheDir(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getcachedir) | Obtain the cache directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetTempDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_gettempdir) | Obtain the temp directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getfilesdir) | Obtain the files directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDatabaseDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getdatabasedir) | Obtain the database directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetPreferencesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getpreferencesdir) | Obtain the preferences directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetBundleCodeDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getbundlecodedir) | Obtain the bundle code directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDistributedFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getdistributedfilesdir) | Obtain the distributed files directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetResourceDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getresourcedir) | Obtain the resource directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCloudFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getcloudfiledir) | Obtain the cloud file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode* areaMode)](#oh_abilityruntime_context_getareamode) | Obtain the area mode of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_SetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode areaMode)](#oh_abilityruntime_context_setareamode) | Set the area mode of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetLogFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getlogfiledir) | Obtain the log file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetProcessName(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getprocessname) | Obtain the process name. |

## Function description

### OH_AbilityRuntime_Context_GetCacheDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCacheDir(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the cache directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get cache directory from. |
| char* buffer | A pointer to a buffer that receives the cache directory of the context. |
| int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetTempDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetTempDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the temp directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get temp directory from. |
| char* buffer | A pointer to a buffer that receives the temp directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the files directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get files directory from. |
| char* buffer | A pointer to a buffer that receives the files directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetDatabaseDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDatabaseDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the database directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get database directory from. |
| char* buffer | A pointer to a buffer that receives the database directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetPreferencesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetPreferencesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the preferences directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get preferences directory from. |
| char* buffer | A pointer to a buffer that receives the preferences directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetBundleCodeDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetBundleCodeDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the bundle code directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get bundle code directory from. |
| char* buffer | A pointer to a buffer that receives the bundle code directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetDistributedFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDistributedFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the distributed files directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get distributed files directory from. |
| char* buffer | A pointer to a buffer that receives the distributed files directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetResourceDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetResourceDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the resource directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get resource directory from. |
| char* buffer | A pointer to a buffer that receives the resource directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetCloudFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCloudFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the cloud file directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get cloud file directory from. |
| char* buffer | A pointer to a buffer that receives the cloud file directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode* areaMode)
```

**Description**

Obtain the area mode of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get the area mode from. |
| AbilityRuntime_AreaMode* areaMode | A pointer to the area mode. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the areaMode is null.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_SetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_SetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode areaMode)
```

**Description**

Set the area mode of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to set the area mode for. |
| AbilityRuntime_AreaMode areaMode | The area mode. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the areaMode is null.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetLogFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetLogFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the log file directory of the context.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get log file directory from. |
| char* buffer | A pointer to a buffer that receives the log file directory of the context. |
| const int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |

### OH_AbilityRuntime_Context_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetProcessName(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtain the process name.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 24

**Parameters**:

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context to get the process name from. |
| char* buffer | A pointer to a buffer that receives the process name. |
| int32_t bufferSize | The length of the buffer. |
| int32_t* writeLength | The string length actually written to the buffer, when returning [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode). |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | The error code.          [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the operation is successful.          [ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the buffer or writeLength is null,          or the buffer size is less than the minimum buffer size.          [ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the context does not exist. |


