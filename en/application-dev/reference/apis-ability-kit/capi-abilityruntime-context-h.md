# context.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @yangzhongkai-->
<!--Designer: @yangzhongkai-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=7b9a2b20c0ccde8a6fcec022ec0fcbcafa6267c4 translatedAt=2026-07-06T02:47:03.625Z pushedAt=2026-07-06T07:59:02.411Z -->

## Overview

Provides the context data structure [AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md) and related APIs for obtaining information such as the app file path, data encryption level, and process name of the current context.

**Reference file:** <AbilityKit/ability_runtime/context.h>

**Library:** libability_runtime.so

**System capability:** SystemCapability.Ability.AbilityRuntime.Core

**Since:** 24

**Related module:** [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [AbilityRuntime_Context](capi-abilityruntime-abilityruntime-context.md) | - | Defines the AbilityRuntime_Context structure type. |
| [AbilityRuntime_Context*](capi-abilityruntime-abilityruntime-context8h.md) | AbilityRuntime_ContextHandle | Defines the AbilityRuntime_Context object pointer. |

### Functions

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCacheDir(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getcachedir) | Gets the cache directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetTempDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_gettempdir) | Gets the temporary file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getfilesdir) | Gets the general file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDatabaseDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getdatabasedir) | Gets the database file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetPreferencesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getpreferencesdir) | Gets the preferences file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetBundleCodeDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getbundlecodedir) | Gets the installation file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDistributedFilesDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getdistributedfilesdir) | Gets the distributed file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetResourceDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getresourcedir) | Gets the resource directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCloudFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getcloudfiledir) | Gets the cloud file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode* areaMode)](#oh_abilityruntime_context_getareamode) | Gets the data encryption level of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_SetAreaMode(AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode areaMode)](#oh_abilityruntime_context_setareamode) | Sets the data encryption level of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetLogFileDir(AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getlogfiledir) | Gets the log file directory of the context. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetProcessName(AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_context_getprocessname) | Gets the process name where the context is located. |

## Function Description

### OH_AbilityRuntime_Context_GetCacheDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCacheDir(
    AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the cache directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context |  The context for which the cache directory is to be obtained. |
| char* buffer | Pointer to the buffer used to receive the cache directory of the context. |
| int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return of [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetCacheDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t cacheDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetCacheDir(context, buffer, 1024, &cacheDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetTempDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetTempDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the temporary file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which the temporary file directory is to be obtained. |
| char* buffer | Pointer to a buffer used to receive the temporary file directory of the context. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetTempDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t tempDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetTempDir(context, buffer, 1024, &tempDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetFilesDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the general file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which to obtain the general file directory. |
| char* buffer | Pointer to the buffer used to receive the general file directory of the context. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size needed to write.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetFilesDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t filesDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetFilesDir(context, buffer, 1024, &filesDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log error and perform other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetDatabaseDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDatabaseDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Gets the database file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | Context for which to get the database file directory. |
| char* buffer | Pointer to buffer, used to receive the database file directory of the context. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetDatabaseDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t databaseDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetDatabaseDir(context, buffer, 1024, &databaseDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log the error and perform other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetPreferencesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetPreferencesDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the preferences file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which the preferences file directory is to be obtained. |
| char* buffer | A pointer to the buffer used to receive the preferences file directory of the context. |
| const int32_t bufferSize | The buffer size, in bytes. |
| int32_t* writeLength | On return of [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetPreferencesDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t preferencesDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetPreferencesDir(context, buffer, 1024, &preferencesDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log the error and perform other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetBundleCodeDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetBundleCodeDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Gets the installation file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which to get the installation file directory. |
| char* buffer | Pointer to buffer, used to receive the installation file directory of the context. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return of [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetBundleCodeDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t bundleCodeDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetBundleCodeDir(context, buffer, 1024, &bundleCodeDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log the error and perform other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetDistributedFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetDistributedFilesDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the distributed file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which the distributed file directory is to be obtained. |
| char* buffer | Pointer to buffer, used to receive the distributed file directory of the context. |
| const int32_t bufferSize | Buffer size, unit: byte. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, unit: byte. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetDistributedFilesDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t distributedFilesDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetDistributedFilesDir(context, buffer, 1024, &distributedFilesDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetResourceDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetResourceDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Gets the resource directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | Context for which to get the resource directory. |
| char* buffer | Pointer to buffer, used to receive the resource directory of the context. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null or context is null, or the buffer size is less than the size needed to write.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetResourceDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t resourceDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetResourceDir(context, buffer, 1024, &resourceDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log error and perform other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetCloudFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetCloudFileDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the cloud file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | Context for which to get the cloud file directory. |
| char* buffer | Pointer to buffer, used to receive the cloud file directory of the context. |
| const int32_t bufferSize | Buffer size, unit: byte. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, unit: byte. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - input parameter buffer or writeLength is null or context is null, or buffer size is less than the size needed to write.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetCloudFileDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t cloudFileDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetCloudFileDir(context, buffer, 1024, &cloudFileDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error log and other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetAreaMode(
    AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode* areaMode)
```

**Description**

Gets the data encryption level of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which to get the data encryption level. |
| [AbilityRuntime_AreaMode](capi-context-constant-h.md#abilityruntime_areamode)* areaMode | Pointer to receive the data encryption level. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter areaMode is null.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetAreaMode(AbilityRuntime_ContextHandle context)
{
    AbilityRuntime_AreaMode areaMode;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetAreaMode(context, &areaMode);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log the error and perform other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_SetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_SetAreaMode(
    AbilityRuntime_ContextHandle context, AbilityRuntime_AreaMode areaMode)
```

**Description**

Sets the data encryption level of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | Context for which the data encryption level is to be set. |
| [AbilityRuntime_AreaMode](capi-context-constant-h.md#abilityruntime_areamode) areaMode | Data encryption level. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter areaMode is null.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testSetAreaMode(AbilityRuntime_ContextHandle context)
{
    AbilityRuntime_AreaMode areaMode = ABILITY_RUNTIME_AREA_MODE_EL1;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_SetAreaMode(context, areaMode);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetLogFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetLogFileDir(
    AbilityRuntime_ContextHandle context, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the log file directory of the context.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which the log file directory is to be obtained. |
| char* buffer | Pointer to a buffer used to receive the log file directory of the context. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size to be written.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetLogFileDir(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t logFileDirSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetLogFileDir(context, buffer, 1024, &logFileDirSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other business processing
    }
    // Normal business processing
}
```

### OH_AbilityRuntime_Context_GetProcessName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_Context_GetProcessName(
    AbilityRuntime_ContextHandle context, char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Gets the process name where the context is located.

**Since:** 24

**Parameters**

| Parameter | Description |
| -- | -- |
| [AbilityRuntime_ContextHandle](capi-abilityruntime-abilityruntime-context8h.md) context | The context for which to obtain the process name. |
| char* buffer | Pointer to a buffer used to receive the process name. |
| int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | On return of [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode), indicates the actual string length written to the buffer, in bytes. |

**Returns:**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Returns the execution result.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - Operation successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter buffer or writeLength is null, or context is null, or the buffer size is less than the size required to write.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - The context does not exist. |

**Example:**

```c
#include <AbilityKit/ability_runtime/context.h>

// Receive a context object
void testGetProcessName(AbilityRuntime_ContextHandle context)
{
    char buffer[1024] = {0};
    int32_t processNameSize = 0;
    AbilityRuntime_ErrorCode errorCode = ABILITY_RUNTIME_ERROR_CODE_NO_ERROR;
    errorCode = OH_AbilityRuntime_Context_GetProcessName(context, buffer, 1024, &processNameSize);
    if (errorCode != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Log error and perform other business processing
    }
    // Normal business processing
}
```