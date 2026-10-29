# native_audio_suite_download_manager.h（系统接口）

## 概述

Declare audio download manager related interfaces.

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSuite_DownloadStatusInfo（系统接口）](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) | - | 定义下载状态信息结构体。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioSuite_DownloadStatusInfoArray（系统接口）](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) | - | 定义下载状态信息数组结构体。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioSuite_FeatureVersionInfo（系统接口）](capi-ohaudiosuite-oh-audiosuite-featureversioninfo-sys.md) | - | 定义特性版本信息结构体。<br>**系统接口：** 此接口为系统接口。 |
| [OH_AudioSuite_DownloadManager（系统接口）](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) | OH_AudioSuite_DownloadManager | 声明音频下载管理器。 音频下载管理器的句柄用于下载相关功能。<br>**系统接口：** 此接口为系统接口。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)（系统接口）](#oh_audiosuite_downloadcallback) | OH_AudioSuite_DownloadCallback | 更新下载状态的回调函数。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)（系统接口）](#oh_audiosuite_getdownloadmanager) | - | 获取音频下载管理器句柄。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)（系统接口）](#oh_audiosuite_registerdownloadcallback) | - | 注册下载状态回调。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)（系统接口）](#oh_audiosuite_unregisterdownloadcallback) | - | 注销下载状态回调。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_startdownload) | - | 开始下载特性。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_pausedownload) | - | 暂停下载特性二进制文件。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_canceldownload) | - | 取消下载特性。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_startbackgrounddownload) | - | 开始后台下载功能。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)（系统接口）](#oh_audiosuite_getdownloadstatus) | - | 获取功能的下载状态。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)（系统接口）](#oh_audiosuite_uninstallcloudrom) | - | 卸载已下载的特性。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_IsFeatureInstalled(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, bool *installStatus, uint32_t installStatusSize)（系统接口）](#oh_audiosuite_isfeatureinstalled) | - | 批量获取特性的安装状态。 接口返回成功，installStatus有效数量为count。失败则installStatus有效数量为0。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_GetFeatureStatus(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_DownloadStatusInfo *statusInfos, uint32_t statusInfosSize)（系统接口）](#oh_audiosuite_getfeaturestatus) | - | 批量获取特性的当前状态。 接口返回成功，statusInfos有效数量为count。失败则statusInfos有效数量为0。<br>**系统接口：** 此接口为系统接口。 |
| [int32_t OH_AudioSuite_GetNewVersionInfo(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_FeatureVersionInfo *versionInfos, uint32_t versionInfosSize)（系统接口）](#oh_audiosuite_getnewversioninfo) | - | 批量获取特性的新版本信息。 接口返回成功，versionInfos有效数量为count。失败则versionInfos有效数量为0。<br>**系统接口：** 此接口为系统接口。 |

### 变量

| 名称 | 描述 |
| -- | -- |
| void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)（系统接口） | 更新下载状态的回调函数。<br>**起始版本：** 26.0.0<br>**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine<br>**系统接口：** 此接口为系统接口。 |

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
| [OH_AudioSuite_DownloadStatusInfoArray](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) *downloadStatusInfoArray | 下载状态信息数组指针。 |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) **downloadManager | 接收下载管理器句柄的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果downloadManager为nullptr。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h.md#oh_audiosuite_downloadcallback) *callback | 接收下载状态更新的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果下载管理器或回调为nullptr，则返回错误。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h.md#oh_audiosuite_downloadcallback) *callback | 注销的回调函数。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果下载管理器或回调为nullptr，则返回错误。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要下载的特性的名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果downloadManager或featureName为nullptr。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

### OH_AudioSuite_PauseDownload()

```c
int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述：**

暂停下载特性二进制文件。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要暂停的功能的名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>{@link AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM如果downloadManager或featureName为nullptr。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要取消的特性名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果downloadManager或featureName为nullptr。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> <li>AVPCOMMON_RESULT_ERROR_LINAL_STATE如果当前状态不允许取消。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要下载的特性的名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果downloadManager或featureName为nullptr。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 特性的名称。 |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *status | 接收下载状态信息的指针。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果downloadManager、featureName或status为nullptr。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

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
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 要卸载的特性名称。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)如果执行成功</li> <li>202如果非系统应用程序调用此系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)如果downloadManager或featureName为nullptr。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result)如果IPC通信失败或操作失败。</li> </ul> |

### OH_AudioSuite_IsFeatureInstalled()

```c
int32_t OH_AudioSuite_IsFeatureInstalled(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, bool *installStatus, uint32_t installStatusSize)
```

**描述：**

批量获取特性的安装状态。 接口返回成功，installStatus有效数量为count。失败则installStatus有效数量为0。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | [入参] 下载管理器句柄。 |
| const char **featureNames | [入参] 特性名称的数组。 |
| uint32_t count | [入参] featureNames数组中特性名称的个数，取值为[1, 5]。 |
| bool *installStatus | [出参] 调用者分配的接收安装状态的布尔数组。元素值为true，表示featureNames对应索引的特性已安装。为false，表示未安装。 |
| uint32_t installStatusSize | [入参] 调用者分配的installStatus输出数组的容量。必须大于等于count。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 执行成功。</li> <li>202 权限验证失败。非系统应用调用系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数为空指针或无效值。可能的原因如下：<ol><li>参数downloadManager为空指针。</li> <li>参数featureNames为空指针。</li> <li>参数featureNames中的值为空指针。</li> <li>参数installStatus为空指针。</li> <li>参数count为0或者大于5。</li> <li>参数installStatusSize小于count。</li></ol> <li>[AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED](capi-native-audio-common-h.md#oh_audiocommon_result) IPC通信失败。</li> </ul> |

### OH_AudioSuite_GetFeatureStatus()

```c
int32_t OH_AudioSuite_GetFeatureStatus(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_DownloadStatusInfo *statusInfos, uint32_t statusInfosSize)
```

**描述：**

批量获取特性的当前状态。 接口返回成功，statusInfos有效数量为count。失败则statusInfos有效数量为0。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | [入参] 下载管理器句柄。 |
| const char **featureNames | [入参] 特性名称的数组。 |
| uint32_t count | [入参] featureNames数组中特性名称的个数，取值为[1, 5]。 |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *statusInfos | [出参] 调用者分配的接收特性状态的数组。 |
| uint32_t statusInfosSize | [入参] 调用者分配的statusInfos输出数组的容量。必须大于等于count。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 执行成功。</li> <li>202 权限验证失败。非系统应用调用系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数为空指针或无效值。可能的原因如下：<ol><li>参数downloadManager为空指针。</li> <li>参数featureNames为空指针。</li> <li>参数featureNames中的值为空指针。</li> <li>参数statusInfos为空指针。</li> <li>参数count为0或者大于5。</li> <li>参数statusInfosSize小于count。</li></ol> <li>[AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED](capi-native-audio-common-h.md#oh_audiocommon_result) IPC通信失败。</li> </ul> |

### OH_AudioSuite_GetNewVersionInfo()

```c
int32_t OH_AudioSuite_GetNewVersionInfo(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_FeatureVersionInfo *versionInfos, uint32_t versionInfosSize)
```

**描述：**

批量获取特性的新版本信息。 接口返回成功，versionInfos有效数量为count。失败则versionInfos有效数量为0。

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanager-sys.md) *downloadManager | [入参] 下载管理器句柄。 |
| const char **featureNames | [入参] 特性名称的数组。 |
| uint32_t count | [入参] featureNames数组中特性名称的个数，取值为[1, 5]。 |
| [OH_AudioSuite_FeatureVersionInfo](capi-ohaudiosuite-oh-audiosuite-featureversioninfo-sys.md) *versionInfos | [出参] 调用者分配的接收版本信息的数组。 |
| uint32_t versionInfosSize | [入参] 调用者分配的输出数组的容量。必须大于等于count。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| int32_t | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 执行成功。</li> <li>202 权限验证失败。非系统应用调用系统API。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) 参数为空指针或无效值。可能的原因如下：<ol><li>参数downloadManager为空指针。</li> <li>参数featureNames为空指针。</li> <li>参数featureNames中的值为空指针。</li> <li>参数versionInfos为空指针。</li> <li>参数count为0或者大于5。</li> <li>参数versionInfosSize小于count。</li></ol> <li>[AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED](capi-native-audio-common-h.md#oh_audiocommon_result) IPC通信失败。</li> <li>[AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET](capi-native-audio-common-h.md#oh_audiocommon_result) 当前网络状态不可用。</li> </ul> |


