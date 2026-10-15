# native_audio_stream_manager.h

## 概述

本文件提供音频流管理功能的接口。 <br>音频流是对系统内音频播放和录制流的统称。音频系统会根据音频流的配置，如播放流的[OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) 和录制流的[OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype)， 为音频流选择合适的音频通路，以达到最佳的音频体验。 <br>在不同设备上，通路支持的情况存在差异，本模块提供了能力查询接口， 开发者可传入待播放或录制音频流的基础属性和用途进行查询。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) | OH_AudioStreamManager | 声明音频流管理结构体，该结构体用于调用系统音频流能力查询功能接口。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)](#oh_audiomanager_getaudiostreammanager) | 获取音频流管理器实例，该实例为单例，用于调用音频流能力查询接口。 |
| [OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)](#oh_audiostreammanager_getdirectplaybacksupport) | 查询当前设备在特定的音频基础格式信息和使用场景下支持的直通通路播放模式。 |
| [OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)](#oh_audiostreammanager_isacousticechocancelersupported) | 查询当前设备在特定的音频录制流使用场景下是否支持回声消除。 |
| [bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isfastplaybacksupported) | 查询当前设备在特定音频播放流信息和使用场景下是否支持低时延播放。 |
| [bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isfastrecordingsupported) | 查询当前设备在特定音频录制流信息和使用场景下是否支持低时延录制。 |
| [bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)](#oh_audiostreammanager_isintelligentnoisereductionenabledforcurrentdevice) | 查询在当前音频设备连接状态下，特定使用场景录音流的智能降噪开关是否已开启。 |
| [bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_ismultichannelplaybacksupported) | 查询当前设备在特定音频播放流信息和使用场景下是否支持多声道播放。 |
| [bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isdirectplaybacksupported) | 查询当前设备在特定音频播放流信息和使用场景下是否支持直通播放。 |
| [bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)](#oh_audiostreammanager_isoffloadplaybacksupported) | 查询当前设备在特定音频播放流信息和使用场景下是否支持低功耗播放。 |

## 函数说明

### OH_AudioManager_GetAudioStreamManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioStreamManager(OH_AudioStreamManager **streamManager)
```

**描述：**

获取音频流管理器实例，该实例为单例，用于调用音频流能力查询接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) **streamManager | [out] 用于接收获取的音频流管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_SYSTEM](capi-native-audio-common-h.md#oh_audiocommon_result) 系统状态错误。</li> </ul> |

### OH_AudioStreamManager_GetDirectPlaybackSupport()

```c
OH_AudioCommon_Result OH_AudioStreamManager_GetDirectPlaybackSupport(OH_AudioStreamManager *audioStreamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage, OH_AudioStream_DirectPlaybackMode *directPlaybackMode)
```

**描述：**

查询当前设备在特定的音频基础格式信息和使用场景下支持的直通通路播放模式。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 19

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *audioStreamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] 音频播放流基础格式信息指针。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 音频播放流使用场景。 |
| [OH_AudioStream_DirectPlaybackMode](capi-native-audiostream-base-h.md#oh_audiostream_directplaybackmode) *directPlaybackMode | [out] 用于获取支持的直通通路播放模式。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) <br>1. 参数audioStreamManager为空指针；<br>2. 参数streamInfo为空指针；<br>3. 参数usage无效；<br>4. 参数directPlaybackMode为空指针。</li> </ul> |

### OH_AudioStreamManager_IsAcousticEchoCancelerSupported()

```c
OH_AudioCommon_Result OH_AudioStreamManager_IsAcousticEchoCancelerSupported(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType sourceType, bool *supported)
```

**描述：**

查询当前设备在特定的音频录制流使用场景下是否支持回声消除。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) sourceType | [in] 音频录制流使用场景。 |
| bool *supported | [out] 用于获取是否支持回声消除的结果。true表示支持，false表示不支持。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result) 函数执行成功。</li> <li>[AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result) <br>1.参数streamManager为空指针；<br>2.参数sourceType无效；<br>3.参数supported为空指针。</li> </ul> |

### OH_AudioStreamManager_IsFastPlaybackSupported()

```c
bool OH_AudioStreamManager_IsFastPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**描述：**

查询当前设备在特定音频播放流信息和使用场景下是否支持低时延播放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] 音频播放流基础格式信息指针。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 音频播放流使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true时表示支持低时延播放，返回false时表示不支持。当输入参数为空指针或无效值时，也会返回false。 |

### OH_AudioStreamManager_IsFastRecordingSupported()

```c
bool OH_AudioStreamManager_IsFastRecordingSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_SourceType source)
```

**描述：**

查询当前设备在特定音频录制流信息和使用场景下是否支持低时延录制。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] 音频录制流基础格式信息指针。 |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | [in] 音频录制流使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true时表示支持低时延录制，返回false时表示不支持。当输入参数为空指针或无效值时，也会返回false。 |

### OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice()

```c
bool OH_AudioStreamManager_IsIntelligentNoiseReductionEnabledForCurrentDevice(OH_AudioStreamManager *streamManager, OH_AudioStream_SourceType source)
```

**描述：**

查询在当前音频设备连接状态下，特定使用场景录音流的智能降噪开关是否已开启。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 21

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStream_SourceType](capi-native-audiostream-base-h.md#oh_audiostream_sourcetype) source | [in] 音频录制流使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true时表示智能降噪开关已打开，返回false时表示开关已关闭。当输入参数为空指针或无效值时，也会返回false。 |

### OH_AudioStreamManager_IsMultichannelPlaybackSupported()

```c
bool OH_AudioStreamManager_IsMultichannelPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**描述：**

查询当前设备在特定音频播放流信息和使用场景下是否支持多声道播放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] 音频播放流基础格式信息指针。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 音频播放流使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true时表示支持多声道播放，返回false时表示不支持。当输入参数为空指针或无效值时，也会返回false。 |

### OH_AudioStreamManager_IsDirectPlaybackSupported()

```c
bool OH_AudioStreamManager_IsDirectPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**描述：**

查询当前设备在特定音频播放流信息和使用场景下是否支持直通播放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] 音频播放流基础格式信息指针。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 音频播放流使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true时表示支持直通播放，返回false时表示不支持。当输入参数为空指针或无效值时，也会返回false。 |

### OH_AudioStreamManager_IsOffloadPlaybackSupported()

```c
bool OH_AudioStreamManager_IsOffloadPlaybackSupported(OH_AudioStreamManager *streamManager, OH_AudioStreamInfo *streamInfo, OH_AudioStream_Usage usage)
```

**描述：**

查询当前设备在特定音频播放流信息和使用场景下是否支持低功耗播放。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioStreamManager](capi-ohaudio-oh-audiostreammanager.md) *streamManager | [in] 通过 [OH_AudioManager_GetAudioStreamManager](capi-native-audio-stream-manager-h.md#oh_audiomanager_getaudiostreammanager)获取的音频流管理器实例。 |
| [OH_AudioStreamInfo](capi-ohaudio-oh-audiostreaminfo.md) *streamInfo | [in] 音频播放流基础格式信息指针。 |
| [OH_AudioStream_Usage](capi-native-audiostream-base-h.md#oh_audiostream_usage) usage | [in] 音频播放流使用场景。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| bool | 返回true时表示支持低功耗播放，返回false时表示不支持。当输入参数为空指针或无效值时，也会返回false。 |


