# application_context.h

## Overview

The file declares the APIs related to the application-level context.

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Function

| Name | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCacheDir(char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcachedir) | Obtains the application-level cache directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetAreaMode(AbilityRuntime_AreaMode* areaMode)](#oh_abilityruntime_applicationcontextgetareamode) | Obtains the application-level file data encryption level of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleName(char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlename) | Obtains the bundle name of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgettempdir) | Obtains the application-level temporary file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetfilesdir) | Obtains the application-level common file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdatabasedir) | Obtains the application-level database file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetpreferencesdir) | Obtains the application-level preferences file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlecodedir) | Obtains the application-level installation file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdistributedfilesdir) | Obtains the application-level distributed file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcloudfiledir) | Obtains the application-level cloud file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetresourcedir) | Obtains the application-level resource directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)](#oh_abilityruntime_startselfuiability) | Starts the UIAbility of the current application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_abilityruntime_startselfuiabilitywithstartoptions) | Starts the UIAbility of the current application using **StartOptions**. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetVersionCode(int64_t* versionCode)](#oh_abilityruntime_applicationcontextgetversioncode) | Obtains the application version code. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLaunchParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlaunchparameter) | Obtains **WantParams** passed for the initial launch of the UIAbility of the current application. For details about **WantParams**, see {@link parameters in Want}. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLatestParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlatestparameter) | Obtains **WantParams** passed for the mose recent launch of the UIAbility of the current application. For details about **WantParams**, see {@link parameters in Want}. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(AbilityBase_Want *want, AbilityRuntime_StartOptions *options, int32_t *targetPid)](#oh_abilityruntime_startselfuiabilitywithpidresult) | Starts the UIAbility of the current application using **StartOptions** and obtains the process ID of the target UIAbility. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLogFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlogfiledir) | Obtains the application-level log file directory of the application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextNotifyPageChanged(const char* targetPageName, int32_t targetPageNameLength, int32_t windowId)](#oh_abilityruntime_applicationcontextnotifypagechanged) | This API can be called only from third-party frameworks. Each time a third-party framework switches pages, it notifies the system of the target page information (including the target page path, the length of the target page path, and the window ID corresponding to the target page). The system can adjust or recover the page according to product policies. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireUIAbilityChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)](#oh_abilityruntime_acquireuiabilitychildprocessinfos) | Acquires UIAbility child process infos of the current application.<br> Includes child processes created via startAbility with ProcessMode.NEW_PROCESS_ATTACH_TO_PARENT. |

## Function description

### OH_AbilityRuntime_ApplicationContextGetCacheDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCacheDir(char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level cache directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the application-level cache directory of the application. |
| int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID:       The passed-in value of buffer or writeLength is null, or the       buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetAreaMode(AbilityRuntime_AreaMode* areaMode)
```

**Description**

Obtains the application-level file data encryption level of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityRuntime_AreaMode* areaMode | Pointer to the encryption level of the received data. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetBundleName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleName(char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the bundle name of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name. |
| int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetTempDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level temporary file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the temporary file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level common file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the common file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetDatabaseDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level database file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the database file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetPreferencesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level preferences file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the preferences file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetBundleCodeDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level installation file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the installation file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level distributed file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the distributed file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetCloudFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level cloud file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 16

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the cloud file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetResourceDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level resource directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 20

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* moduleName | Pointer to the module name. |
| char* buffer | Pointer to the buffer, which is used to receive the resource directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)
```

**Description**

Starts the UIAbility of the current application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permission**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 15

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityBase_Want *want | Pointer to the Want information required for starting the UIAbility. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED: Permission verification for the caller fails.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: Parameter verification for the caller fails.       ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED: The device type is not supported.       ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY: The specified ability name does not exist.       ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE: The ability type is incorrect.       ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED: The crowdtesting application expires.       ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE: The ability is started or stopped in Wukong mode.       ABILITY_RUNTIME_ERROR_CODE_CONTROLLED: The application is under control.       ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED: The application is under control by EDM.       ABILITY_RUNTIME_ERROR_CODE_CROSS_APP: Redirecting to third-party applications       is not allowed in API versions later than 11.       ABILITY_RUNTIME_ERROR_CODE_INTERNAL: An internal error occurs.       ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY: The application is not a top one.       ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED (available since API version 17):       The number of instances has reached the upper limit.       ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED (available since API version 17): Setting        APP_INSTANCE_KEY is not supported.       For details, see AbilityRuntime_ErrorCode. |

### OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want, AbilityRuntime_StartOptions *options)
```

**Description**

Starts the UIAbility of the current application using **StartOptions**.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permission**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 17

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityBase_Want *want | Pointer to the Want information required for starting the UIAbility. |
| AbilityRuntime_StartOptions *options | Pointer to **StartOptions** required for starting the UIAbility. If the value of {@link startVisibility} is not null, ensure that the current application has been added to the status bar. Otherwise, the [ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) error code is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul><li>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED: Permission verification for the caller fails.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: Parameter verification for the caller fails.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED: The device type is not supported.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY: The specified ability name does not exist.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE: The ability type is incorrect.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED: The crowdtesting application expires.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE: The ability is started or stopped in Wukong mode.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_CONTROLLED: The application is under control.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED: The application is under control by EDM.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_CROSS_APP: Redirecting to third-party applications       is not allowed in API versions later than 11.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_INTERNAL: An internal error occurs.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY: The application is not a top one.</li>       <li>ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED:       Setting the window visibility during startup is not allowed.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED:       The application does not support clone or multi-instance mode.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY: The multi-instance key is invalid.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED:       The number of instances has reached the upper limit.</li>       <li>ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED:       The application does not support multi-instance mode.</li>       <li>ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED:       Setting APP_INSTANCE_KEY is not supported.       For details, see AbilityRuntime_ErrorCode.</li></ul> |

### OH_AbilityRuntime_ApplicationContextGetVersionCode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetVersionCode(int64_t* versionCode)
```

**Description**

Obtains the application version code.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| int64_t* versionCode | The version code of the application. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: versionCode is null.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application.       ABILITY_RUNTIME_ERROR_CODE_GET_APPLICATION_INFO_FAILED: Failed to obtain the application information. |

### OH_AbilityRuntime_ApplicationContextGetLaunchParameter()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLaunchParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains **WantParams** passed for the initial launch of the UIAbility of the current application. For details about **WantParams**, see {@link parameters in Want}.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive **WantParams**. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextGetLatestParameter()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLatestParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains **WantParams** passed for the mose recent launch of the UIAbility of the current application. For details about **WantParams**, see {@link parameters in Want}.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive **WantParams**. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_StartSelfUIAbilityWithPidResult()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(AbilityBase_Want *want, AbilityRuntime_StartOptions *options, int32_t *targetPid)
```

**Description**

Starts the UIAbility of the current application using **StartOptions** and obtains the process ID of the target UIAbility.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Required permission**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 21

**Parameters**:

| Parameter | Description |
| -- | -- |
| AbilityBase_Want *want | Pointer to the Want information required for starting the UIAbility. |
| AbilityRuntime_StartOptions *options | Pointer to **StartOptions** required for starting the UIAbility. If the value of {@link startVisibility} is not null, ensure that the current application has been added to the status bar. Otherwise, the [ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) error code is returned. |
| int32_t *targetPid | Pointer to the process ID of the target UIAbility. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED: Permission verification for the caller fails.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: Parameter verification for the caller fails.       ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED: The device type is not supported.       ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY: The specified ability name does not exist.       ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE: The ability type is incorrect.       ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED: The crowdtesting application expires.       ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE: The ability is started or stopped in Wukong mode.       ABILITY_RUNTIME_ERROR_CODE_CONTROLLED: The application is under control.       ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED: The application is under control by EDM.       ABILITY_RUNTIME_ERROR_CODE_CROSS_APP: Redirecting to third-party applications       is not allowed in API versions later than 11.       ABILITY_RUNTIME_ERROR_CODE_INTERNAL: An internal error occurs.       ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY: The application is not a top one.       ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED:       Setting the window visibility during startup is not allowed.       ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED:       The application does not support clone or multi-instance mode.       ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY: The multi-instance key is invalid.       ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED: The number of instances has reached the upper limit.       ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED: The application does not support multi-instance mode.       ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED: Setting APP_INSTANCE_KEY is not supported.       ABILITY_RUNTIME_ERROR_CODE_START_TIMEOUT: Starting the UIAbility times out.       ABILITY_RUNTIME_ERROR_CODE_MAIN_THREAD_NOT_SUPPORTED:       The function cannot be called on the main thread of the application. |

### OH_AbilityRuntime_ApplicationContextGetLogFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLogFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level log file directory of the application.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 22

**Parameters**:

| Parameter | Description |
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the log file directory. |
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The passed-in value of buffer or writeLength is null,       or the buffer size is less than the size of the string to be written.       ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST: The application context does not exist. For example, the       application-level context does not exist in the {@link child process} created by the application. |

### OH_AbilityRuntime_ApplicationContextNotifyPageChanged()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextNotifyPageChanged(const char* targetPageName, int32_t targetPageNameLength, int32_t windowId)
```

**Description**

This API can be called only from third-party frameworks. Each time a third-party framework switches pages, it notifies the system of the target page information (including the target page path, the length of the target page path, and the window ID corresponding to the target page). The system can adjust or recover the page according to product policies.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 23

**Parameters**:

| Parameter | Description |
| -- | -- |
| const char* targetPageName | Target page path. |
| int32_t targetPageNameLength | Length of the target page path. |
| int32_t windowId | {@link Window ID} corresponding to the target page. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | One of the following execution results:       ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.       ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID:       The input parameter targetPageName is empty orthe windowId is invalid.       ABILITY_RUNTIME_ERROR_CODE_INTERNAL: An internal error occurs. |

### OH_AbilityRuntime_AcquireUIAbilityChildProcessInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireUIAbilityChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)
```

**Description**

Acquires UIAbility child process infos of the current application.<br> Includes child processes created via startAbility with ProcessMode.NEW_PROCESS_ATTACH_TO_PARENT.

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 26.0.1

**Parameters**:

| Parameter | Description |
| -- | -- |
| OH_AbilityRuntime_ChildProcessInfosHandle* infos | [out] Pointer to child process info collection. It must not be NULL. When no child processes exist, the dereferenced value of the pointer **infos** is set to nullptr. |
| uint32_t* count | [out] Pointer to the number of child processes. It must not be NULL. |

**Returns**:

| Type | Description |
| -- | -- |
| AbilityRuntime_ErrorCode | <ul>       <li>[ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the call is successful.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if the arguments provided are invalid.</li>       <li>[ABILITY_RUNTIME_ERROR_CODE_INTERNAL](capi-ability-runtime-common-h.md#abilityruntime_errorcode) if an internal error occurs,       such as connect system service failed.</li>       </ul> |


