# native_audio_suite_download_manager.h（系统接口）

## 概述

Declare audio download manager related interfaces.

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**相关模块：** [AudioSuite](capi-audiosuite.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSuite_DownloadStatusInfo（系统接口）](capi-audiosuite-oh-audiosuite-downloadstatusinfo-sys.md) | OH_AudioSuite_DownloadStatusInfo | 定义下载状态信息结构体。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioSuite_DownloadStatusInfoArray（系统接口）](capi-audiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) | OH_AudioSuite_DownloadStatusInfoArray | 定义下载状态信息数组结构体。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioSuite_DownloadManagerStruct（系统接口）](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) | OH_AudioSuite_DownloadManager | 声明音频下载管理器。 音频下载管理器的句柄用于下载相关功能。<br>**系统接口：** 此接口为系统接口。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)（系统接口）](#oh_audiosuite_downloadcallback) | OH_AudioSuite_DownloadCallback | 更新下载状态的回调函数。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)（系统接口）](#oh_audiosuite_getdownloadmanager) | - | 获取音频下载管理器句柄。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)（系统接口）](#oh_audiosuite_registerdownloadcallback) | - | 注册下载状态回调。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)（系统接口）](#oh_audiosuite_unregisterdownloadcallback) | - | 注销下载状态回调。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_startdownload) | - | 开始下载特性。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_canceldownload) | - | 取消下载特性。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_startbackgrounddownload) | - | 开始后台下载功能。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)（系统接口）](#oh_audiosuite_getdownloadstatus) | - | 获取功能的下载状态。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_uninstallcloudrom) | - | 卸载已下载的特性。<br>**系统接口：** 此接口为系统接口。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)（系统接口） | 更新下载状态的回调函数。<br>**起始版本：** 26.0.0<br>**系统接口：** 此接口为系统接口。 |

## 函数说明

### OH_AudioSuite_DownloadCallback()

```c
typedef void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)
```

**描述：**

更新下载状态的回调函数。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadStatusInfoArray](capi-audiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) \*downloadStatusInfoArray | 下载状态信息数组指针。 |

### OH_AudioSuite_GetDownloadManager()

```c
int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)
```

**描述：**

获取音频下载管理器句柄。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) **downloadManager | 接收下载管理器句柄的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果downloadManager为nullptr。</li>  </ul> |

### OH_AudioSuite_RegisterDownloadCallback()

```c
int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**描述：**

注册下载状态回调。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h.md#oh_audiosuite_downloadcallback) *callback | 接收下载状态更新的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果下载管理器或回调为nullptr，则返回错误。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li>  </ul> |

### OH_AudioSuite_UnregisterDownloadCallback()

```c
int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**描述：**

注销下载状态回调。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h.md#oh_audiosuite_downloadcallback) *callback | 注销的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果下载管理器或回调为nullptr，则返回错误。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li>  </ul> |

### OH_AudioSuite_StartDownload()

```c
int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述：**

开始下载特性。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要下载的特性的名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果downloadManager或featureName为nullptr。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li>  </ul> |

### OH_AudioSuite_CancelDownload()

```c
int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述：**

取消下载特性。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要取消的特性名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果downloadManager或featureName为nullptr。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li><br><li>{@link AVPCOMMON_RESULT_ERROR_LINAL_STATE}如果当前状态不允许取消。</li>  </ul> |

### OH_AudioSuite_StartBackgroundDownload()

```c
int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述：**

开始后台下载功能。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要下载的特性的名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果downloadManager或featureName为nullptr。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li>  </ul> |

### OH_AudioSuite_GetDownloadStatus()

```c
int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)
```

**描述：**

获取功能的下载状态。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 特性的名称。 |
| [OH_AudioSuite_DownloadStatusInfo](capi-audiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *status | 接收下载状态信息的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果downloadManager、featureName或status为nullptr。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li>  </ul> |

### OH_AudioSuite_UninstallCloudRom()

```c
int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述：**

卸载已下载的特性。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-audiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要卸载的特性名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul>  <li>{@link AUDIOCOMMON_RESULT_SUCCESS}如果执行成功</li><br><li>202如果非系统应用程序调用此系统API。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM}如果downloadManager或featureName为nullptr。</li><br><li>{@link AUDIOCOMMON_RESULT_ERROR_SYSTEM}如果IPC通信失败或操作失败。</li>  </ul> |


