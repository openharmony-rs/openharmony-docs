# application_context.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @lixueqing513-->
<!--Adviser: @huipeizi-->

## Overview

The file declares the APIs related to the application-level context.

**File to include**: <AbilityKit/ability_runtime/application_context.h>

**Library**: libability_runtime.so

**System capability**: SystemCapability.Ability.AbilityRuntime.Core

**Since**: 13

**Related module**: [AbilityRuntime](capi-abilityruntime.md)

## Summary

### Functions

| Name| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCacheDir(char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcachedir) | Obtains the application-level cache directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetAreaMode(AbilityRuntime_AreaMode* areaMode)](#oh_abilityruntime_applicationcontextgetareamode) | Obtains the application-level file data encryption level of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleName(char* buffer, int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlename) | Obtains the bundle name of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgettempdir) | Obtains the application-level temporary file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetfilesdir) | Obtains the application-level common file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdatabasedir) | Obtains the application-level database file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetpreferencesdir) | Obtains the application-level preferences file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlecodedir) | Obtains the application-level installation file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdistributedfilesdir) | Obtains the application-level distributed file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcloudfiledir) | Obtains the application-level cloud file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLogFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlogfiledir) | Obtains the application-level log file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetresourcedir) | Obtains the application-level resource directory of the application.    |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)](#oh_abilityruntime_startselfuiability) | Starts the UIAbility of the current application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want,AbilityRuntime_StartOptions *options)](#oh_abilityruntime_startselfuiabilitywithstartoptions) | Starts the UIAbility of the current application using **StartOptions**.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetVersionCode(int64_t* versionCode)](#oh_abilityruntime_applicationcontextgetversioncode) | Obtains the application version code.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(AbilityBase_Want *want, AbilityRuntime_StartOptions *options, int32_t *targetPid)](#oh_abilityruntime_startselfuiabilitywithpidresult) | Starts the UIAbility of the current application using **StartOptions** and obtains the process ID of the target UIAbility.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLaunchParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlaunchparameter) | Obtains **WantParams** passed for the initial launch of the UIAbility of the current application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLatestParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlatestparameter)| Obtains **WantParams** passed for the most recent launch of the UIAbility of the current application.|

## Function Description

### OH_AbilityRuntime_ApplicationContextGetCacheDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCacheDir(char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level cache directory of the application.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the application-level cache directory of the application.|
| int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetAreaMode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetAreaMode(AbilityRuntime_AreaMode* areaMode)
```

**Description**

Obtains the application-level file data encryption level of the application.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityRuntime_AreaMode](capi-context-constant-h.md#abilityruntime_areamode)* areaMode | Pointer to the encryption level of the received data.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetBundleName()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleName(char* buffer, int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the bundle name of the application.

**Since**: 13

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetTempDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level temporary file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level common file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetDatabaseDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level database file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetPreferencesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level preferences file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetBundleCodeDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level installation file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level distributed file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetCloudFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level cloud file directory of the application.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetLogFileDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLogFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level log file directory of the application.

**Since**: 22

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the log file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_ApplicationContextGetResourceDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level resource directory of the application.

**Since**: 20

**Parameters**

| Name| Description|
| -- | -- |
| char* moduleName | Pointer to the module name.|
| char* buffer | Pointer to the buffer, which is used to receive the bundle name.|
| int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

### OH_AbilityRuntime_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)
```

**Description**

Starts the UIAbility of the current application.


**Required permissions**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 15

**Device behavior differences**: This API can be properly called only on 2-in-1 devices and tablets. If it is called on other device types, error code **ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED** is returned.

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityBase_Want](capi-abilitybase-want.md) *want | Pointer to the Want information required for starting the UIAbility.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED**: Permission verification for the caller fails.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: Parameter verification for the caller fails.<br>**ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED**: The device type is not supported.<br>**ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY**: The specified ability name does not exist.<br>**ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE**: The ability type is incorrect.<br>**ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED**: The crowdtesting application expires.<br>**ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE**: The ability is started or stopped in Wukong mode.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTROLLED**: The application is under control.<br>**ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED**: The application is under control by EDM.<br>**ABILITY_RUNTIME_ERROR_CODE_CROSS_APP**: Redirecting to third-party applications is not allowed in API versions later than 11.<br>**ABILITY_RUNTIME_ERROR_CODE_INTERNAL**: An internal error occurs.<br>**ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY**: The application is not a top one.<br>**ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED** (available since API version 17): The number of instances has reached the upper limit.<br>**ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED** (available since API version 17): Setting **APP_INSTANCE_KEY** is not supported.<br>For details, see **AbilityRuntime_ErrorCode**.|

**Example**

```cpp
#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>

void startSelfUIAbilityTest()
{
    AbilityBase_Element element;
    element.abilityName = const_cast<char*>("EntryAbility");
    element.bundleName = const_cast<char*>("com.example.myapplication");
    element.moduleName = const_cast<char*>("entry");
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);

    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_StartSelfUIAbility(want);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
        return;
    }
    // Destroy the Want to prevent memory leakage.
    OH_AbilityBase_DestroyWant(want);
}
```

### OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want,AbilityRuntime_StartOptions *options)
```

**Description**

Starts the UIAbility of the current application using **StartOptions**.

**Required permissions**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 17

**Device behavior differences**: This API can be properly called only on 2-in-1 devices and tablets. If it is called on other device types, error code **ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED** is returned.

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityBase_Want](capi-abilitybase-want.md) *want | Pointer to the Want information required for starting the UIAbility.|
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *options | Pointer to **StartOptions** required for starting the UIAbility. If the value of [startVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) is not null, ensure that the current application has been added to the status bar. Otherwise, the [ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) error code is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED**: Permission verification for the caller fails.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: Parameter verification for the caller fails.<br>**ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED**: The device type is not supported.<br>**ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY**: The specified ability name does not exist.<br>**ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE**: The ability type is incorrect.<br>**ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED**: The crowdtesting application expires.<br>**ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE**: The ability is started or stopped in Wukong mode.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTROLLED**: The application is under control.<br>**ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED**: The application is under control by EDM.<br>**ABILITY_RUNTIME_ERROR_CODE_CROSS_APP**: Redirecting to third-party applications is not allowed in API versions later than 11.<br>**ABILITY_RUNTIME_ERROR_CODE_INTERNAL**: An internal error occurs.<br>**ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY**: The application is not a top one.<br>**ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED**: Setting the window visibility during startup is not allowed.<br>**ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED**: The application does not support clone or multi-instance mode.<br>**ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY**: The multi-instance key is invalid.<br> **ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED**: The number of instances has reached the upper limit.<br>**ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED**: The application does not support multi-instance mode.<br>**ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED**: Setting **APP_INSTANCE_KEY** is not supported.<br>For details, see **AbilityRuntime_ErrorCode**.|

**Example**

```cpp
#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>

void demo()
{
    AbilityBase_Element element;
    element.abilityName = const_cast<char*>("EntryAbility");
    element.bundleName = const_cast<char*>("com.example.myapplication");
    element.moduleName = const_cast<char*>("entry");
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);
    if (want == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.

        // Destroy the Want to prevent memory leakage.
        OH_AbilityBase_DestroyWant(want);
        return;
    }
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(want, options);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy the Want to prevent memory leakage.
    OH_AbilityBase_DestroyWant(want);

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_ApplicationContextGetVersionCode()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetVersionCode(int64_t* versionCode)
```

**Description**

Obtains the application version code.

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| int64_t* [versionCode](js-apis-bundleManager-bundleInfo.md#bundleinfo-1) | Pointer to the bundle's version code, which corresponds to the **versionCode** field in **bundleInfo**.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: **versionCode** is null.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.<br>**ABILITY_RUNTIME_ERROR_CODE_GET_APPLICATION_INFO_FAILED**: Failed to obtain the application information.|

### OH_AbilityRuntime_StartSelfUIAbilityWithPidResult()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(AbilityBase_Want *want, AbilityRuntime_StartOptions *options, int32_t *targetPid)
```

**Description**

Starts the UIAbility of the current application using **StartOptions** and obtains the process ID of the target UIAbility.

This function cannot be called on the main thread of an application, but can be called on the main thread of a [child process](capi-childprocess.md) created by the application.

If it is called on the main thread of the application, error code **ABILITY_RUNTIME_ERROR_CODE_MAIN_THREAD_NOT_SUPPORTED** is returned.

**Required permissions**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 21

**Device behavior differences**: This API can be properly called only on 2-in-1 devices and tablets. If it is called on other device types, error code **ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED** is returned.

**Parameters**

| Name| Description|
| -- | -- |
| [AbilityBase_Want](capi-abilitybase-want.md) *want | Pointer to the Want information required for starting the UIAbility.|
| [AbilityRuntime_StartOptions](capi-abilityruntime-startoptions.md) *options | Pointer to **StartOptions** required for starting the UIAbility. If the value of [startVisibility](capi-context-constant-h.md#abilityruntime_startvisibility) is not null, ensure that the current application has been added to the status bar. Otherwise, the [ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED](capi-ability-runtime-common-h.md#abilityruntime_errorcode) error code is returned.|
| int32_t *targetPid | Pointer to the process ID of the target UIAbility.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | **ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PERMISSION_DENIED**: Permission verification for the caller fails.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: Parameter verification for the caller fails.<br>**ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED**: The device type is not supported.<br>**ABILITY_RUNTIME_ERROR_CODE_NO_SUCH_ABILITY**: The specified ability name does not exist.<br>**ABILITY_RUNTIME_ERROR_CODE_INCORRECT_ABILITY_TYPE**: The ability type is incorrect.<br>**ABILITY_RUNTIME_ERROR_CODE_CROWDTEST_EXPIRED**: The crowdtesting application expires.<br>**ABILITY_RUNTIME_ERROR_CODE_WUKONG_MODE**: The ability is started or stopped in Wukong mode.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTROLLED**: The application is under control.<br>**ABILITY_RUNTIME_ERROR_CODE_EDM_CONTROLLED**: The application is under control by EDM.<br>**ABILITY_RUNTIME_ERROR_CODE_CROSS_APP**: Redirecting to third-party applications is not allowed in API versions later than 11.<br>**ABILITY_RUNTIME_ERROR_CODE_INTERNAL**: An internal error occurs.<br>**ABILITY_RUNTIME_ERROR_CODE_NOT_TOP_ABILITY**: The application is not a top one.<br>**ABILITY_RUNTIME_ERROR_VISIBILITY_SETTING_DISABLED**: Setting the window visibility during startup is not allowed.<br>**ABILITY_RUNTIME_ERROR_CODE_MULTI_APP_NOT_SUPPORTED**: The application does not support clone or multi-instance mode.<br>**ABILITY_RUNTIME_ERROR_CODE_INVALID_APP_INSTANCE_KEY**: The multi-instance key is invalid.<br> **ABILITY_RUNTIME_ERROR_CODE_UPPER_LIMIT_REACHED**: The number of instances has reached the upper limit.<br>**ABILITY_RUNTIME_ERROR_MULTI_INSTANCE_NOT_SUPPORTED**: The application does not support multi-instance mode.<br>**ABILITY_RUNTIME_ERROR_CODE_APP_INSTANCE_KEY_NOT_SUPPORTED**: Setting **APP_INSTANCE_KEY** is not supported.<br>**ABILITY_RUNTIME_ERROR_CODE_START_TIMEOUT**: Starting the UIAbility times out.<br>**ABILITY_RUNTIME_ERROR_CODE_MAIN_THREAD_NOT_SUPPORTED**: The function cannot be called on the main thread of the application.|

**Example**

```cpp
#include <AbilityKit/ability_base/want.h>
#include <AbilityKit/ability_runtime/application_context.h>

void demo()
{
    AbilityBase_Element element;
    element.abilityName = const_cast<char*>("EntryAbility");
    element.bundleName = const_cast<char*>("com.example.myapplication");
    element.moduleName = const_cast<char*>("entry");
    AbilityBase_Want* want = OH_AbilityBase_CreateWant(element);
    if (want == nullptr) {
        // Record error logs and other service processing.
        return;
    }

    AbilityRuntime_StartOptions* options = OH_AbilityRuntime_CreateStartOptions();
    if (options == nullptr) {
        // Record error logs and other service processing.

        // Destroy the Want to prevent memory leakage.
        OH_AbilityBase_DestroyWant(want);
        return;
    }
    int32_t pid = -1;
    AbilityRuntime_ErrorCode err = OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(want, options, &pid);
    if (err != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Record error logs and other service processing.
    }
    // Destroy the Want to prevent memory leakage.
    OH_AbilityBase_DestroyWant(want);

    // Destroy options to prevent memory leakage.
    OH_AbilityRuntime_DestroyStartOptions(&options);
}
```

### OH_AbilityRuntime_ApplicationContextGetLaunchParameter

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLaunchParameter(
    char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains **WantParams** passed for the initial launch of the UIAbility of the current application. For details about **WantParams**, see [parameters in Want](js-apis-inner-ability-want.md).

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive **WantParams**.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

**Example**
```cpp
#include "napi/native_api.h"
#include "AbilityKit/ability_runtime/application_context.h"

static napi_value GetLaunchParameter(napi_env env, napi_callback_info info)
{
    const int32_t bufferSize = 2048; // Adjust the buffer size as required.
    char buffer[bufferSize] = {0};
    int32_t writeLength = 0;
    int32_t ret = OH_AbilityRuntime_ApplicationContextGetLaunchParameter(buffer, bufferSize, &writeLength);

    if (ret != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Handle exceptions.
    }
    // Create a JS string and return WantParams.
    napi_value result;
    napi_create_string_utf8(env, buffer, writeLength, &result);
    return result;
}
```

### OH_AbilityRuntime_ApplicationContextGetLatestParameter

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLatestParameter(
    char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains **WantParams** passed for the mose recent launch of the UIAbility of the current application. For details about **WantParams**, see [parameters in Want](js-apis-inner-ability-want.md).

**Since**: 21

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive **WantParams**.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>**ABILITY_RUNTIME_ERROR_CODE_NO_ERROR**: The operation is successful.<br>**ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID**: The passed-in value of **buffer** or **writeLength** is null, or the buffer size is less than the size of the string to be written.<br>**ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST**: The application context does not exist. For example, the application-level context does not exist in the [child process](capi-childprocess.md) created by the application.|

**Example**
```cpp
#include "napi/native_api.h"
#include "AbilityKit/ability_runtime/application_context.h"

static napi_value GetLatestParameter(napi_env env, napi_callback_info info)
{
    const int32_t bufferSize = 2048; // Adjust the buffer size as required.
    char buffer[bufferSize] = {0};
    int32_t writeLength = 0;
    int32_t ret = OH_AbilityRuntime_ApplicationContextGetLatestParameter(buffer, bufferSize, &writeLength);

    if (ret != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Handle exceptions.
    }
    // Create a JS string and return WantParams.
    napi_value result;
    napi_create_string_utf8(env, buffer, writeLength, &result);
    return result;
}
```

### OH_AbilityRuntime_ApplicationContextNotifyPageChanged

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextNotifyPageChanged(
    const char* targetPageName, int32_t targetPageNameLength, int32_t windowId)
```

**Description**

This API can be called only from third-party frameworks. Each time a third-party framework switches pages, it notifies the system of the target page information (including the target page path, the length of the target page path, and the window ID corresponding to the target page). The system can adjust or recover the page according to product policies.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const char* targetPageName | Target page path.|
| int32_t targetPageNameLength | Length of the target page path.|
| int32_t windowId | [Window ID](../apis-arkui/arkts-apis-window-i.md#windowinfo18) corresponding to the target page.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | One of the following execution results:<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR: The operation is successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID: The input parameter **targetPageName** is empty or the windowId is invalid.<br>**ABILITY_RUNTIME_ERROR_CODE_INTERNAL**: An internal error occurs.|

**Example**
```cpp
#include "napi/native_api.h"
#include "AbilityKit/ability_runtime/application_context.h"

static bool NotifyPageChanged(napi_env env, napi_callback_info info)
{
    const char* testPageName = "https://home.taobao.com/homepage";
    int32_t testPageNameLen = 32;
    int32_t testWindowId = 12; // The sample value is for reference only. Use a valid window ID in actual development.
    int32_t ret = OH_AbilityRuntime_ApplicationContextNotifyPageChanged(testPageName, testPageNameLen, testWindowId);

    if (ret != ABILITY_RUNTIME_ERROR_CODE_NO_ERROR) {
        // Handle exceptions.
        return false;
    }
    return true;
}
```
