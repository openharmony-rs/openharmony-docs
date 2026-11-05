# native_audio_suite_download_manager.h (System API)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=96c2f543d580d0d2b2dabb53953551af3ab0252e translatedAt=2026-11-03T03:57:33.805Z pushedAt=2026-11-04T03:11:46.960Z nl=1 -->

## Overview

Declares the APIs related to the audio download manager.

**File to include:** <ohaudiosuite/native_audio_suite_download_manager.h>

**Library:** libohaudiosuite.so

**System capability:** SystemCapability.Multimedia.Audio.SuiteEngine

**Since:** 26.0.0

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Structs

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) | OH_AudioSuite_DownloadStatusInfo | Defines the download status information struct. |
| [OH_AudioSuite_DownloadStatusInfoArray](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) | OH_AudioSuite_DownloadStatusInfoArray | Defines the download status information array struct. |
| [OH_AudioSuite_DownloadManagerStruct](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) | OH_AudioSuite_DownloadManager | Declares the audio download manager.<br> The handle of the audio download manager is used to perform download-related functions. |
| [OH_AudioSuite_FeatureVersionInfo](capi-ohaudiosuite-oh-audiosuite-featureversioninfo-sys.md) | OH_AudioSuite_FeatureVersionInfo | Defines the feature version information struct. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)](#oh_audiosuite_downloadcallback) | OH_AudioSuite_DownloadCallback | Callback for download status updates. |
| [int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)](#oh_audiosuite_getdownloadmanager) | - | Obtains the audio download manager handle, which is obtained by OH_AudioSuite_GetDownloadManager and used to identify the operation target in subsequent calls to download-related APIs. |
| [int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)](#oh_audiosuite_registerdownloadcallback) | - | Registers the download status callback. |
| [int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)](#oh_audiosuite_unregisterdownloadcallback) | - | Unregisters the download status callback. |
| [int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_startdownload) | - | Starts the download. |
| [int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_pausedownload) | - | Pauses the download. |
| [int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_canceldownload) | - | Cancels the download. |
| [int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_startbackgrounddownload) | - | Starts the background download. |
| [int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)](#oh_audiosuite_getdownloadstatus) | - | Obtains the download status. |
| [int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_uninstallcloudrom) | - | Uninstalls the downloaded cloud file. |
| [int32_t OH_AudioSuite_IsFeatureInstalled(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, bool *installStatus, uint32_t installStatusSize)](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_isfeatureinstalled) | - | Obtains the installation status of features in batches. |
| [int32_t OH_AudioSuite_GetFeatureStatus(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_DownloadStatusInfo *statusInfos, uint32_t statusInfosSize)](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_getfeaturestatus) | - | Obtains the feature status in batches. |
| [int32_t OH_AudioSuite_GetNewVersionInfo(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_FeatureVersionInfo *versionInfos, uint32_t versionInfosSize)](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_getnewversioninfo) | - | Obtains the new version information of features in batches. |

## Function Description

### OH_AudioSuite_DownloadCallback()

```c
typedef void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)
```

**Description**

Callback for the download status update.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadStatusInfoArray](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) *downloadStatusInfoArray | Pointer to the download status information array. |

### OH_AudioSuite_GetDownloadManager()

```c
int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)
```

**Description**

Obtains the audio download manager handle, which is obtained by OH_AudioSuite_GetDownloadManager and used to identify the operation target in subsequent calls to download-related APIs.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) **downloadManager | Pointer to the download manager handle to be received. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager is a null pointer. |

### OH_AudioSuite_RegisterDownloadCallback()

```c
int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**Description**

Registers the download status callback.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle to the download manager. |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_downloadcallback) *callback | Callback invoked to return the download status update. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         Returns AUDIOCOMMON_RESULT_SUCCESS if the operation is executed successfully.<br>         Returns 202 if a non-system application calls this system API.<br>         Returns AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM if the download manager or the callback is a null pointer.<br>         Returns AUDIOCOMMON_RESULT_ERROR_SYSTEM if IPC communication fails or the operation fails. |

### OH_AudioSuite_UnregisterDownloadCallback()

```c
int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**Description**

Unregisters the download status callback.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle of the download manager. |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_downloadcallback) *callback | Callback for the download status event to be unregistered. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager or the callback is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication failure or operation failure. |

### OH_AudioSuite_StartDownload()

```c
int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Starts downloading.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle of the download manager. |
| const char *featureName | Name of the cloud file to download. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication failure or operation failure. |

### OH_AudioSuite_PauseDownload()

```c
int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Pauses the download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle of the download manager. |
| const char *featureName | Name of the cloud file to be paused. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         **AUDIOCOMMON_RESULT_SUCCESS**: The operation is successful.<br>         **202**: A non-system app calls this system API.<br>         **AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM**: The download manager or the cloud file name is a null pointer.<br>         **AUDIOCOMMON_RESULT_ERROR_SYSTEM**: IPC failure or operation failure. |

### OH_AudioSuite_CancelDownload()

```c
int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Cancels the download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle of the download manager. |
| const char *featureName | Name of the cloud file to cancel. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication failure or operation failure.<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: the current state does not allow cancellation. |

### OH_AudioSuite_StartBackgroundDownload()

```c
int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Starts a background download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle of the download manager. |
| const char *featureName | Name of the cloud file to download. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication failure or operation failure. |

### OH_AudioSuite_GetDownloadStatus()

```c
int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)
```

**Description**

Obtains the download status.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle to the download manager. |
| const char *featureName | Cloud file name. |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *status | Pointer to the download status information. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager, cloud file name, or status pointer is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication failure or operation failure. |

### OH_AudioSuite_UninstallCloudRom()

```c
int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Uninstalls the downloaded cloud file.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Handle of the download manager. |
| const char *featureName | Name of the cloud file to uninstall. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: a non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the download manager or cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication failure or operation failure. |

### OH_AudioSuite_IsFeatureInstalled()

```c
int32_t OH_AudioSuite_IsFeatureInstalled(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, bool *installStatus, uint32_t installStatusSize)
```

**Description**

Obtains the installation status of features in batches.

If the API returns success, the valid count of installStatus is count. If it fails, the valid count of installStatus is 0.

**Since:** 26.0.1

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | [in] Download Manager handle. |
| const char **featureNames | [in] Array of feature names. |
| uint32_t count | [in] Count of feature names in the featureNames array. The value range is [1, 5]. |
| bool *installStatus | [out] Boolean array allocated by the caller to receive the installation status. A value of true indicates that the feature at the corresponding index in featureNames is installed. A value of false indicates that it is not installed. |
| uint32_t installStatusSize | [in] Capacity of the installStatus output array allocated by the caller. It must be greater than or equal to count. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: permission verification failed. A non-system application calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: a parameter is a null pointer or an invalid value.<br>         Possible causes:<br>         1. The downloadManager parameter is a null pointer.<br>         2. The featureNames parameter is a null pointer.<br>         3. A value in the featureNames parameter is a null pointer.<br>         4. The installStatus parameter is a null pointer.<br>         5. The count parameter is 0 or greater than 5.<br>         6. The installStatusSize parameter is less than count.<br>         AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED: IPC communication failure. |

### OH_AudioSuite_GetFeatureStatus()

```c
int32_t OH_AudioSuite_GetFeatureStatus(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_DownloadStatusInfo *statusInfos, uint32_t statusInfosSize)
```

**Description**

Obtains the current status of features in batches.

If the API returns success, the valid count of statusInfos is count. If it fails, the valid count of statusInfos is 0.

**Since:** 26.0.1

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | [in] Download manager handle. |
| const char **featureNames | [in] Array of feature names. |
| uint32_t count | [in] Number of feature names in the featureNames array. The value ranges from 1 to 5. |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *statusInfos | [out] Array allocated by the caller to receive the feature status. |
| uint32_t statusInfosSize | [in] Capacity of the statusInfos output array allocated by the caller. It must be greater than or equal to count. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: permission verification failed. A non-system application calls a system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the parameter is a null pointer or an invalid value.<br>         Possible causes are as follows:<br>         1. The downloadManager parameter is a null pointer.<br>         2. The featureNames parameter is a null pointer.<br>         3. A value in the featureNames parameter is a null pointer.<br>         4. The statusInfos parameter is a null pointer.<br>         5. The count parameter is 0 or greater than 5.<br>         6. The statusInfosSize parameter is less than count.<br>AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED: IPC communication failure. |

### OH_AudioSuite_GetNewVersionInfo()

```c
int32_t OH_AudioSuite_GetNewVersionInfo(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_FeatureVersionInfo *versionInfos, uint32_t versionInfosSize)
```

**Description**

Obtains the new version information of features in batches.

If the API returns success, the valid count of versionInfos is count. If it fails, the valid count of versionInfos is 0.

**Since:** 26.0.1

**System API:** This is a system API.

**Parameters**

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | [in] Download Manager handle. |
| const char **featureNames | [in] Array of feature names. |
| uint32_t count | [in] Count of feature names in the featureNames array. The value ranges from 1 to 5. |
| [OH_AudioSuite_FeatureVersionInfo](capi-ohaudiosuite-oh-audiosuite-featureversioninfo-sys.md) *versionInfos | [out] Array allocated by the caller to receive the version information. |
| uint32_t versionInfosSize | [in] Capacity of the output array allocated by the caller. It must be greater than or equal to count. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS: executed successfully.<br>         202: permission verification failed. A non-system application calls a system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: the parameter is a null pointer or an invalid value.<br>         Possible causes are as follows:<br>         1. The downloadManager parameter is a null pointer.<br>         2. The featureNames parameter is a null pointer.<br>         3. A value in the featureNames parameter is a null pointer.<br>         4. The versionInfos parameter is a null pointer.<br>         5. The count parameter is 0 or greater than 5.<br>         6. The versionInfosSize parameter is less than count.<br>         AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED: IPC communication failure.<br>         AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET: the current network status is unavailable. |
