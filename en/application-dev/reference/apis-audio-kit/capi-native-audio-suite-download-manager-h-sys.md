# native_audio_suite_download_manager.h (System API)

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b9233046c3f90e6ca45044fd6224c6d08e2aa256 translatedAt=2026-08-31T02:33:16.662Z pushedAt=2026-08-31T09:07:40.247Z -->

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
| [OH_AudioSuite_DownloadManagerStruct](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) | OH_AudioSuite_DownloadManager | Declares the audio download manager.<br> The handle to the audio download manager is used to perform download-related functions. |

### Functions

| Name | typedef Keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)](#oh_audiosuite_downloadcallback) | OH_AudioSuite_DownloadCallback | Defines the callback for download status updates. |
| [int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)](#oh_audiosuite_getdownloadmanager) | - | Obtains the handle to the audio download manager, which is obtained by OH_AudioSuite_GetDownloadManager and used to identify the operation target in subsequent calls to download-related APIs. |
| [int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)](#oh_audiosuite_registerdownloadcallback) | - | Registers the download status callback. |
| [int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)](#oh_audiosuite_unregisterdownloadcallback) | - | Unregisters the download status callback. |
| [int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_startdownload) | - | Starts a download. |
| [int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_pausedownload) | - | Pauses a download. |
| [int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_canceldownload) | - | Cancels a download. |
| [int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_startbackgrounddownload) | - | Starts a background download. |
| [int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)](#oh_audiosuite_getdownloadstatus) | - | Obtains the download status. |
| [int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_uninstallcloudrom) | - | Uninstalls a downloaded cloud file. |

## Function Description

### OH_AudioSuite_DownloadCallback()

```c
typedef void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)
```

**Description**

Callback for download status updates.

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) **downloadManager | Pointer to the download manager handle to receive. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager is a null pointer. |

### OH_AudioSuite_RegisterDownloadCallback()

```c
int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**Description**

Registers the download status callback.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_downloadcallback) *callback | Callback function for receiving download status updates.|

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or callback is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC communication fails or the operation fails. |

### OH_AudioSuite_UnregisterDownloadCallback()

```c
int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**Description**

Unregisters the download status callback.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_downloadcallback) *callback | Callback to unregister. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or callback is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails. |

### OH_AudioSuite_StartDownload()

```c
int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Starts a download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the cloud file to download. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails. |

### OH_AudioSuite_PauseDownload()

```c
int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Pauses a download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the cloud file to be paused. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails. |

### OH_AudioSuite_CancelDownload()

```c
int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Cancels a download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the cloud file to cancel. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails.<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE: The current state does not allow cancellation. |

### OH_AudioSuite_StartBackgroundDownload()

```c
int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Starts a background download.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the cloud file to download. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails. |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the cloud file. |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *status | Pointer to the download status information to receive. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | Result code.<br>         AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager, cloud file name, or status pointer is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails. |

### OH_AudioSuite_UninstallCloudRom()

```c
int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Uninstalls a downloaded cloud file.

**Since:** 26.0.0

**System API:** This is a system API.

**Parameters**

| Name | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the cloud file to uninstall. |

**Return**

| Type | Description |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS: Success.<br>         202: A non-system app calls this system API.<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM: The download manager or the cloud file name is a null pointer.<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM: IPC fails or the operation fails. |