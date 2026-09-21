# native_audio_suite_download_manager.h(System API)

## Overview

Declare audio download manager related interfaces.

**Library**: libohaudiosuite.so

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

## Summary

### Struct

| Name | typedef keyword | Description |
| -- | -- | -- |
| [OH_AudioSuite_DownloadStatusInfo(System API)](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) | OH_AudioSuite_DownloadStatusInfo | Define download status information structure.<br>**System API:** This is a system API. |
| [OH_AudioSuite_DownloadStatusInfoArray(System API)](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) | OH_AudioSuite_DownloadStatusInfoArray | Define download status information array structure.<br>**System API:** This is a system API. |
| [OH_AudioSuite_DownloadManagerStruct(System API)](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) | OH_AudioSuite_DownloadManager | Declare the audio download manager. The handle of audio download manager is used for download related functions.<br>**System API:** This is a system API. |

### Function

| Name | typedef keyword | Description |
| -- | -- | -- |
| [typedef void (\*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)(System API)](#oh_audiosuite_downloadcallback) | OH_AudioSuite_DownloadCallback | Callback function for download status update.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)(System API)](#oh_audiosuite_getdownloadmanager) | - | Get the audio download manager handle.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)(System API)](#oh_audiosuite_registerdownloadcallback) | - | Register download status callback.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)(System API)](#oh_audiosuite_unregisterdownloadcallback) | - | Unregister download status callback.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)(System API)](#oh_audiosuite_startdownload) | - | Start downloading a feature.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)(System API)](#oh_audiosuite_pausedownload) | - | Pause downloading a feature.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)(System API)](#oh_audiosuite_canceldownload) | - | Cancel downloading a feature.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)(System API)](#oh_audiosuite_startbackgrounddownload) | - | Start background downloading a feature.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)(System API)](#oh_audiosuite_getdownloadstatus) | - | Get download status of a feature.<br>**System API:** This is a system API. |
| [int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)(System API)](#oh_audiosuite_uninstallcloudrom) | - | Uninstall a downloaded feature.<br>**System API:** This is a system API. |

### Variable

| Name | Description |
| -- | -- |
| void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)(System API) | Callback function for download status update.<br>**Since**: 26.0.0<br>**System API:** This is a system API. |

## Function description

### OH_AudioSuite_DownloadCallback()

```c
typedef void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)
```

**Description**

Callback function for download status update.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadStatusInfoArray](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) \*downloadStatusInfoArray | Pointer to array of download status information. |

### OH_AudioSuite_GetDownloadManager()

```c
int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)
```

**Description**

Get the audio download manager handle.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) **downloadManager | Pointer to receive the download manager handle. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager is nullptr.</li>          </ul> |

### OH_AudioSuite_RegisterDownloadCallback()

```c
int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**Description**

Register download status callback.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h.md#oh_audiosuite_downloadcallback) *callback | Callback function to receive download status updates. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or callback is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |

### OH_AudioSuite_UnregisterDownloadCallback()

```c
int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**Description**

Unregister download status callback.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h.md#oh_audiosuite_downloadcallback) *callback | Callback function to unregister. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or callback is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |

### OH_AudioSuite_StartDownload()

```c
int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Start downloading a feature.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the feature to download. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or featureName is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |

### OH_AudioSuite_PauseDownload()

```c
int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Pause downloading a feature.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the feature to pause. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or featureName is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |

### OH_AudioSuite_CancelDownload()

```c
int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Cancel downloading a feature.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the feature to cancel. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or featureName is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE} If the current state does not allow cancellation.</li>          </ul> |

### OH_AudioSuite_StartBackgroundDownload()

```c
int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Start background downloading a feature.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the feature to download. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or featureName is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |

### OH_AudioSuite_GetDownloadStatus()

```c
int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)
```

**Description**

Get download status of a feature.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the feature. |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *status | Pointer to receive download status information. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager, featureName or status is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |

### OH_AudioSuite_UninstallCloudRom()

```c
int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**Description**

Uninstall a downloaded feature.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Parameters**:

| Parameter | Description |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | Download manager handle. |
| const char *featureName | Name of the feature to uninstall. |

**Returns**:

| Type | Description |
| -- | -- |
| int32_t | <ul>          <li>{@link AUDIOCOMMON_RESULT_SUCCESS} If the execution is successful.</li><br>        <li>202 if a non-system application calls this system API.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} If downloadManager or featureName is nullptr.</li><br>        <li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM} If IPC communication fails or the operation fails.</li>          </ul> |


