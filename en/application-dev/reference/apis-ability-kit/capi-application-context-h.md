# application_context.h

<!--Kit: Ability Kit-->
<!--Subsystem: Ability-->
<!--Owner: @zexin_c-->
<!--Designer: @li-weifeng2024-->
<!--Tester: @liangchengguang-->
<!--Adviser: @HelloCrease-->
<!-- md-trans-meta sourceCommit=f0ca4679538114d37c428618ebeb98dcc5067c5b translatedAt=2026-09-03T08:42:06.580Z pushedAt=2026-09-05T10:47:30.100Z -->

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
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgettempdir) | Gets the application-level temporary file directory of the current application. This directory is used to store temporary files during application running, which may be deleted when the application exits or the system performs cleanup. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetfilesdir) | Gets the application-level general file directory of the current application. This directory is used to store files that need to be persisted by the application, such as user-generated documents, downloaded files, and application data. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDatabaseDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdatabasedir) | Obtains the application-level database file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetPreferencesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetpreferencesdir) | Obtains the application-level preferences file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetBundleCodeDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetbundlecodedir) | Obtains the application-level installation file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetDistributedFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetdistributedfilesdir) | Obtains the application-level distributed file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetCloudFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetcloudfiledir) | Obtains the application-level cloud file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLogFileDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlogfiledir) | Obtains the application-level log file directory of the application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetResourceDir(const char* moduleName, char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetresourcedir) | Gets the application-level resource directory of the current application. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)](#oh_abilityruntime_startselfuiability) | Starts the UIAbility of the current application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithStartOptions(AbilityBase_Want *want, AbilityRuntime_StartOptions *options)](#oh_abilityruntime_startselfuiabilitywithstartoptions) | Starts the UIAbility of the current app with StartOptions. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetVersionCode(int64_t* versionCode)](#oh_abilityruntime_applicationcontextgetversioncode) | Obtains the application version code.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(AbilityBase_Want *want, AbilityRuntime_StartOptions *options, int32_t *targetPid)](#oh_abilityruntime_startselfuiabilitywithpidresult) | Starts the UIAbility of the current application using **StartOptions** and obtains the process ID of the target UIAbility.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLaunchParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlaunchparameter) | Obtains **WantParams** passed for the initial launch of the UIAbility of the current application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLatestParameter(char* buffer, const int32_t bufferSize, int32_t* writeLength)](#oh_abilityruntime_applicationcontextgetlatestparameter)| Obtains **WantParams** passed for the most recent launch of the UIAbility of the current application.|
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextNotifyPageChanged(const char* targetPageName, int32_t targetPageNameLength, int32_t windowId)](#oh_abilityruntime_applicationcontextnotifypagechanged) | This API is only supported for third-party framework calls. Each time the third-party framework switches pages, it notifies the system of the target page information (including the target page path, target page path length, and the window ID corresponding to the target page). This enables the system to perceive which page the current application window is on, thereby performing page management. |
| [AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireUIAbilityChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)](#oh_abilityruntime_acquireuiabilitychildprocessinfos) | Gets the UIAbility child process information of the current application. |

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if areaMode is null.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

### OH_AbilityRuntime_ApplicationContextGetTempDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetTempDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level temporary file directory of the current application. This directory is used to store temporary files during application running, which may be deleted when the application exits or the system cleans up.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the temporary file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - query success.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

### OH_AbilityRuntime_ApplicationContextGetFilesDir()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetFilesDir(char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the application-level general file directory of the current application. This directory is used to store files that need to be persisted by the application, such as user-generated documents, downloaded files, and application data.

**Since**: 16

**Parameters**

| Name| Description|
| -- | -- |
| char* buffer | Pointer to the buffer, which is used to receive the common file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - query success.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| char* buffer | Pointer to the buffer, which is used to receive the database file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - query success.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| char* buffer | Pointer to the buffer, which is used to receive the preferences file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| char* buffer | Pointer to the buffer, which is used to receive the installation file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| char* buffer | Pointer to the buffer, which is used to receive the distributed file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - query success.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST - the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| char* buffer | Pointer to the buffer, which is used to receive the cloud file directory.|
| const int32_t bufferSize | Buffer size, in bytes.|
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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
| const char* moduleName | Module name, used to specify the target module whose resource directory is to be obtained. Developers can obtain the list of module names contained in the application through the bundleManager module APIs. Different module names correspond to different resource directory paths. |
| char* buffer | Pointer to the buffer, which is used to receive the resource directory.|
| const int32_t bufferSize | Buffer size, in bytes. |
| int32_t* writeLength | Pointer to the length of the string written to the buffer (measured in bytes) when [ABILITY_RUNTIME_ERROR_CODE_NO_ERROR](capi-ability-runtime-common-h.md#abilityruntime_errorcode) is returned.|

**Returns**

| Type| Description|
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

### OH_AbilityRuntime_StartSelfUIAbility()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbility(AbilityBase_Want *want)
```

**Description**

Starts the UIAbility of the current application.


**Required permissions**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 15

**Device behavior difference**: This API can be called normally only on PC/2in1 and Tablet devices. On other devices, it returns the ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED error code.

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

**Device behavior difference**: This API can be called normally only on PC/2in1 and Tablet devices. On other devices, it returns the ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED error code.

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter versionCode is null.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application.<br>Returns ABILITY_RUNTIME_ERROR_CODE_GET_APPLICATION_INFO_FAILED if getting the application information fails, for example, the application is not installed or the application information is corrupted. |

### OH_AbilityRuntime_StartSelfUIAbilityWithPidResult()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_StartSelfUIAbilityWithPidResult(AbilityBase_Want *want, AbilityRuntime_StartOptions *options, int32_t *targetPid)
```

**Description**

Starts the UIAbility of the current application using **StartOptions** and obtains the process ID of the target UIAbility.

This API cannot be called on the main thread of the application, but can be called on the main thread of the [ChildProcess](capi-childprocess.md) created by the application.

If it is called on the main thread of the application, error code **ABILITY_RUNTIME_ERROR_CODE_MAIN_THREAD_NOT_SUPPORTED** is returned.

**Required permissions**: ohos.permission.NDK_START_SELF_UI_ABILITY

**Since**: 21

**Device behavior difference**: This API can be called normally only on PC/2in1 and Tablet devices. On other devices, it returns the ABILITY_RUNTIME_ERROR_CODE_NOT_SUPPORTED error code.

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

### OH_AbilityRuntime_ApplicationContextGetLaunchParameter()

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query is successful.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application.|

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

### OH_AbilityRuntime_ApplicationContextGetLatestParameter()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextGetLatestParameter(
    char* buffer, const int32_t bufferSize, int32_t* writeLength)
```

**Description**

Obtains the WantParams parameters used when the current application last started a UIAbility. For details about WantParams, see [parameters in Want](js-apis-inner-ability-want.md). This API is applicable to scenarios where the parameters passed at the last startup need to be obtained, such as processing the latest startup request and parsing page redirection parameters.

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
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>Returns ABILITY_RUNTIME_ERROR_CODE_NO_ERROR if the query succeeds.<br>Returns ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID if the input parameter buffer or writeLength is null, or the buffer size is smaller than the required write size.<br>Returns ABILITY_RUNTIME_ERROR_CODE_CONTEXT_NOT_EXIST if the application context does not exist, for example, the application-level context does not exist in the [ChildProcess](capi-childprocess.md) created by the application. |

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

### OH_AbilityRuntime_ApplicationContextNotifyPageChanged()

```cpp
AbilityRuntime_ErrorCode OH_AbilityRuntime_ApplicationContextNotifyPageChanged(
    const char* targetPageName, int32_t targetPageNameLength, int32_t windowId)
```

**Description**

This API only supports calls from third-party frameworks. Each time a third-party framework switches pages, it notifies the system of the target page information (including the target page path, target page path length, and window ID corresponding to the target page). The system can adjust or restore the page based on the product policy. This API is applicable to scenarios such as page navigation tracking, page state synchronization, and system-level page optimization for third-party frameworks.

**Since**: 23

**Parameters**

| Name| Description|
| -- | -- |
| const char* targetPageName | Target page path.|
| int32_t targetPageNameLength | Length of the target page path.|
| int32_t windowId | Window ID in [WindowInfo](../apis-arkui/arkts-apis-window-i.md#windowinfo18) corresponding to the target page.|

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

### OH_AbilityRuntime_AcquireUIAbilityChildProcessInfos()

```c
AbilityRuntime_ErrorCode OH_AbilityRuntime_AcquireUIAbilityChildProcessInfos(OH_AbilityRuntime_ChildProcessInfosHandle* infos, uint32_t* count)
```

**Description**

Obtains the UIAbility child process information of the current application, including the child processes started through the [startSelfUIAbilityInChildProcess](js-apis-inner-application-uiAbilityContext.md#startselfuiabilityinchildprocess) API, and the child processes started through the [startAbility](js-apis-inner-application-uiAbilityContext.md#startability-2) API with [processMode](js-apis-app-ability-contextConstant.md#processmode12) in [StartOptions](js-apis-app-ability-startOptions.md) set to NEW_PROCESS_ATTACH_TO_PARENT.

After the obtained `infos` is used, call [OH_AbilityRuntime_ReleaseChildProcessInfos](capi-child-process-info-h.md#oh_abilityruntime_releasechildprocessinfos) to release it to avoid memory leaks.

**Since:** 26.1.0

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AbilityRuntime_ChildProcessInfosHandle](capi-nativechildprocess-infos.md)* infos | Output parameter. Pointer to the handle of the child process information set. It cannot be nullptr. After a successful call, `*infos` points to the child process information set. After use, call [OH_AbilityRuntime_ReleaseChildProcessInfos](capi-child-process-info-h.md#oh_abilityruntime_releasechildprocessinfos) to release it. |
| uint32_t* count | Output parameter. Number of child processes. It cannot be nullptr. After a successful call, `*count` indicates the number of UIAbility child processes of the current application. If there is no child process, `*count` is 0. |

**Return**

| Type | Description |
| -- | -- |
| [AbilityRuntime_ErrorCode](capi-ability-runtime-common-h.md#abilityruntime_errorcode) | Result code.<br>ABILITY_RUNTIME_ERROR_CODE_NO_ERROR - The operation is successful.<br>ABILITY_RUNTIME_ERROR_CODE_PARAM_INVALID - The input parameter infos or count is nullptr.<br>ABILITY_RUNTIME_ERROR_CODE_INTERNAL - An internal error occurs, for example, failed to connect to the system service.<br>For details, see AbilityRuntime_ErrorCode. |