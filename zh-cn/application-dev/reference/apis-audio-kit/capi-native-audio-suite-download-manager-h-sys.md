# native_audio_suite_download_manager.h（系统接口）
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频下载管理器相关接口。

**引用文件：** <ohaudiosuite/native_audio_suite_download_manager.h>

**库：** libohaudiosuite.so

**系统能力：** SystemCapability.Multimedia.Audio.SuiteEngine

**起始版本：** 26.0.0

**相关模块：** [OHAudioSuite](capi-ohaudiosuite.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) | OH_AudioSuite_DownloadStatusInfo | 定义下载状态信息结构。 |
| [OH_AudioSuite_DownloadStatusInfoArray](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) | OH_AudioSuite_DownloadStatusInfoArray | 定义下载状态信息数组结构。 |
| [OH_AudioSuite_DownloadManagerStruct](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) | OH_AudioSuite_DownloadManager | 声明音频下载管理器。<br> 音频下载管理器的句柄用于执行下载相关功能。 |
| [OH_AudioSuite_FeatureVersionInfo](capi-ohaudiosuite-oh-audiosuite-featureversioninfo-sys.md) | OH_AudioSuite_FeatureVersionInfo | 定义特性版本信息结构体。 |

### 函数

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [typedef void (\*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)](#oh_audiosuite_downloadcallback) | OH_AudioSuite_DownloadCallback | 下载状态更新的回调函数。 |
| [int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)](#oh_audiosuite_getdownloadmanager) | - | 获取音频下载管理器句柄，由OH_AudioSuite_GetDownloadManager获取，用于后续调用下载相关接口时标识操作目标。 |
| [int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)](#oh_audiosuite_registerdownloadcallback) | - | 注册下载状态回调。 |
| [int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)](#oh_audiosuite_unregisterdownloadcallback) | - | 取消注册下载状态回调。 |
| [int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_startdownload) | - | 开始下载。 |
| [int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_pausedownload) | - | 暂停下载。 |
| [int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_canceldownload) | - | 取消下载。 |
| [int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_startbackgrounddownload) | - | 后台下载。 |
| [int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)](#oh_audiosuite_getdownloadstatus) | - | 获取下载状态。 |
| [int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)](#oh_audiosuite_uninstallcloudrom) | - | 卸载已下载的云端文件。 |
| [int32_t OH_AudioSuite_IsFeatureInstalled(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, bool *installStatus, uint32_t installStatusSize)](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_isfeatureinstalled) | - | 批量获取特性的安装状态。 |
| [int32_t OH_AudioSuite_GetFeatureStatus(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_DownloadStatusInfo *statusInfos, uint32_t statusInfosSize)](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_getfeaturestatus) | - | 批量获取特性状态。 |
| [int32_t OH_AudioSuite_GetNewVersionInfo(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_FeatureVersionInfo *versionInfos, uint32_t versionInfosSize)](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_getnewversioninfo) | - | 批量获取特性的新版本信息。 |

## 函数说明

### OH_AudioSuite_DownloadCallback()

```c
typedef void (*OH_AudioSuite_DownloadCallback)(OH_AudioSuite_DownloadStatusInfoArray *downloadStatusInfoArray)
```

**描述**

下载状态更新的回调函数。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadStatusInfoArray](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfoarray-sys.md) *downloadStatusInfoArray | 指向下载状态信息数组的指针。 |

### OH_AudioSuite_GetDownloadManager()

```c
int32_t OH_AudioSuite_GetDownloadManager(OH_AudioSuite_DownloadManager **downloadManager)
```

**描述**

获取音频下载管理器句柄，由OH_AudioSuite_GetDownloadManager获取，用于后续调用下载相关接口时标识操作目标。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) **downloadManager | 指向接收下载管理器句柄的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器为空指针。 |

### OH_AudioSuite_RegisterDownloadCallback()

```c
int32_t OH_AudioSuite_RegisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**描述**

注册下载状态回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_downloadcallback) *callback | 接收下载状态更新的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或回调函数为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_UnregisterDownloadCallback()

```c
int32_t OH_AudioSuite_UnregisterDownloadCallback(OH_AudioSuite_DownloadManager *downloadManager, const OH_AudioSuite_DownloadCallback *callback)
```

**描述**

取消注册下载状态回调。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| [const OH_AudioSuite_DownloadCallback](capi-native-audio-suite-download-manager-h-sys.md#oh_audiosuite_downloadcallback) *callback | 需要取消注册的回调函数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或回调函数为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_StartDownload()

```c
int32_t OH_AudioSuite_StartDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述**

开始下载。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 需要下载的云端文件名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或云端文件名称为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_PauseDownload()

```c
int32_t OH_AudioSuite_PauseDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述**

暂停下载。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 需要暂停的云端文件名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或云端文件名称为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_CancelDownload()

```c
int32_t OH_AudioSuite_CancelDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述**

取消下载。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 需要取消的云端文件名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或云端文件名称为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。<br>         AUDIOCOMMON_RESULT_ERROR_ILLEGAL_STATE：当前状态不允许取消。 |

### OH_AudioSuite_StartBackgroundDownload()

```c
int32_t OH_AudioSuite_StartBackgroundDownload(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述**

后台下载。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 需要下载的云端文件名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或云端文件名称为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_GetDownloadStatus()

```c
int32_t OH_AudioSuite_GetDownloadStatus(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName, OH_AudioSuite_DownloadStatusInfo *status)
```

**描述**

获取下载状态。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 云端文件名称。 |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *status | 指向接收下载状态信息的指针。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器、云端文件名称或状态指针为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_UninstallCloudRom()

```c
int32_t OH_AudioSuite_UninstallCloudRom(OH_AudioSuite_DownloadManager *downloadManager, const char *featureName)
```

**描述**

卸载已下载的云端文件。

**起始版本：** 26.0.0

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | 下载管理器句柄。 |
| const char *featureName | 需要卸载的云端文件名称。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：非系统应用调用此系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：下载管理器或云端文件名称为空指针。<br>         AUDIOCOMMON_RESULT_ERROR_SYSTEM：IPC通信失败或操作失败。 |

### OH_AudioSuite_IsFeatureInstalled()

```c
int32_t OH_AudioSuite_IsFeatureInstalled(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, bool *installStatus, uint32_t installStatusSize)
```

**描述**

批量获取特性的安装状态。

接口返回成功，installStatus有效数量为count。失败则installStatus有效数量为0。

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | [入参] 下载管理器句柄。 |
| const char **featureNames | [入参] 特性名称的数组。 |
| uint32_t count | [入参] featureNames数组中特性名称的个数，取值为[1, 5]。 |
| bool *installStatus | [出参] 调用者分配的接收安装状态的布尔数组。元素值为true，表示featureNames对应索引的特性已安装。为false，表示未安装。 |
| uint32_t installStatusSize | [入参] 调用者分配的installStatus输出数组的容量。必须大于等于count。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：权限验证失败。非系统应用调用系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数为空指针或无效值。<br>         可能的原因如下：<br>         1. 参数downloadManager为空指针；<br>         2. 参数featureNames为空指针；<br>         3. 参数featureNames中的值为空指针；<br>         4. 参数installStatus为空指针；<br>         5. 参数count为0或者大于5；<br>         6. 参数installStatusSize小于count。<br>         AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED：IPC通信失败。 |

### OH_AudioSuite_GetFeatureStatus()

```c
int32_t OH_AudioSuite_GetFeatureStatus(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_DownloadStatusInfo *statusInfos, uint32_t statusInfosSize)
```

**描述**

批量获取特性的当前状态。

接口返回成功，statusInfos有效数量为count。失败则statusInfos有效数量为0。

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | [入参] 下载管理器句柄。 |
| const char **featureNames | [入参] 特性名称的数组。 |
| uint32_t count | [入参] featureNames数组中特性名称的个数，取值为[1, 5]。 |
| [OH_AudioSuite_DownloadStatusInfo](capi-ohaudiosuite-oh-audiosuite-downloadstatusinfo-sys.md) *statusInfos | [出参] 调用者分配的接收特性状态的数组。 |
| uint32_t statusInfosSize | [入参] 调用者分配的statusInfos输出数组的容量。必须大于等于count。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：权限验证失败。非系统应用调用系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数为空指针或无效值。<br>         可能的原因如下：<br>         1. 参数downloadManager为空指针；<br>         2. 参数featureNames为空指针；<br>         3. 参数featureNames中的值为空指针；<br>         4. 参数statusInfos为空指针；<br>         5. 参数count为0或者大于5；<br>         6. 参数statusInfosSize小于count。<br>AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED：IPC通信失败。 |

### OH_AudioSuite_GetNewVersionInfo()

```c
int32_t OH_AudioSuite_GetNewVersionInfo(OH_AudioSuite_DownloadManager *downloadManager, const char **featureNames, uint32_t count, OH_AudioSuite_FeatureVersionInfo *versionInfos, uint32_t versionInfosSize)
```

**描述**

批量获取特性的新版本信息。

接口返回成功，versionInfos有效数量为count。失败则versionInfos有效数量为0。

**起始版本：** 26.0.1

**系统接口：** 此接口为系统接口。

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioSuite_DownloadManager](capi-ohaudiosuite-oh-audiosuite-downloadmanagerstruct-sys.md) *downloadManager | [入参] 下载管理器句柄。 |
| const char **featureNames | [入参] 特性名称的数组。 |
| uint32_t count | [入参] featureNames数组中特性名称的个数，取值为[1, 5]。 |
| [OH_AudioSuite_FeatureVersionInfo](capi-ohaudiosuite-oh-audiosuite-featureversioninfo-sys.md) *versionInfos | [出参] 调用者分配的接收版本信息的数组。 |
| uint32_t versionInfosSize | [入参] 调用者分配的输出数组的容量。必须大于等于count。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| int32_t | AUDIOCOMMON_RESULT_SUCCESS：执行成功。<br>         202：权限验证失败。非系统应用调用系统API。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数为空指针或无效值。<br>         可能的原因如下：<br>         1. 参数downloadManager为空指针；<br>         2. 参数featureNames为空指针；<br>         3. 参数featureNames中的值为空指针；<br>         4. 参数versionInfos为空指针；<br>         5. 参数count为0或者大于5；<br>         6. 参数versionInfosSize小于count。<br>         AUDIOCOMMON_RESULT_ERROR_SERVICE_DIED：IPC通信失败。<br>         AUDIOCOMMON_RESULT_ERROR_NETWORK_CONDITION_NOT_MET：当前网络状态不可用。 |
