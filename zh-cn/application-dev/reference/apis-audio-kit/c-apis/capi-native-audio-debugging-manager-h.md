# native_audio_debugging_manager.h

## 概述

本文件提供适用于音频调试场景使用的接口。 <br>针对音频开发的特点和常见问题，系统将开发者调试音频功能所需要的系统内部信息通过接口提供出去， 便于开发者查看应用内音频业务对象的状态，用于定位用户音频功能问题。 <br>使用调试接口首先需要通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager) 获取音频调试管理器实例，通过该对象调用其他音频调试接口，包括应用快照、音频播放快照、音频录制快照等。

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) | OH_AudioDebuggingManager | 声明音频调试管理结构体，该结构体用于调用输出音频调试信息功能接口。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)](#oh_audiomanager_getaudiodebuggingmanager) | 获取音频调试管理器实例，该实例为单例，用于调用其他音频调试功能接口。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)](#oh_audiodebuggingmanager_printappinfo) | 打印当前进程中所有音频模块的快照信息。 <br>应用快照包含当前应用进程中所有播放快照、录音快照、耳返快照和会话快照信息，是不同场景快照的汇总， 适用于需要一次性获取整体音频运行状态的场景。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)](#oh_audiodebuggingmanager_printrendererinfo) | 打印指定音频播放实例的快照信息。 <br>音频播放快照记录播放流参数、通路信息、音量、设备信息、焦点状态、历史错误记录等信息， 适用于排查播放无声、音量异常、焦点被抢占等问题。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)](#oh_audiodebuggingmanager_printcapturerinfo) | 打印指定录音实例的快照信息。 <br>录音快照记录录音流参数、通路信息、录音时间戳、设备信息、溢出计数、历史错误记录等信息， 适用于排查录音无数据、录音卡顿等问题。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)](#oh_audiodebuggingmanager_printsessioninfo) | 打印指定音频会话的快照信息。 <br>音频会话快照记录会话状态、并发策略、场景类型、设备信息、关联音频流等信息， 适用于排查会话激活异常、并发策略不生效等问题。 |

## 函数说明

### OH_AudioManager_GetAudioDebuggingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)
```

**描述：**

获取音频调试管理器实例，该实例为单例，用于调用其他音频调试功能接口。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) **manager | [out] 指向OH_AudioDebuggingManager指针的地址，用于接收音频调试管理器实例。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为空指针。</li> </ul> |

### OH_AudioDebuggingManager_PrintAppInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)
```

**描述：**

打印当前进程中所有音频模块的快照信息。 <br>应用快照包含当前应用进程中所有播放快照、录音快照、耳返快照和会话快照信息，是不同场景快照的汇总， 适用于需要一次性获取整体音频运行状态的场景。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [in] 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| int32_t fd | [in] 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为空指针。</li> </ul> |

### OH_AudioDebuggingManager_PrintRendererInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)
```

**描述：**

打印指定音频播放实例的快照信息。 <br>音频播放快照记录播放流参数、通路信息、音量、设备信息、焦点状态、历史错误记录等信息， 适用于排查播放无声、音量异常、焦点被抢占等问题。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [in] 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorenderer.md) *renderer | [in] 指向目标音频播放实例的指针，用于打印快照信息。 |
| int32_t fd | [in] 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager或renderer为空指针。</li> </ul> |

### OH_AudioDebuggingManager_PrintCapturerInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)
```

**描述：**

打印指定录音实例的快照信息。 <br>录音快照记录录音流参数、通路信息、录音时间戳、设备信息、溢出计数、历史错误记录等信息， 适用于排查录音无数据、录音卡顿等问题。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [in] 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturer.md) *capturer | [in] 指向目标录音实例的指针，用于打印快照信息。 |
| int32_t fd | [in] 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager或capturer为空指针。</li> </ul> |

### OH_AudioDebuggingManager_PrintSessionInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)
```

**描述：**

打印指定音频会话的快照信息。 <br>音频会话快照记录会话状态、并发策略、场景类型、设备信息、关联音频流等信息， 适用于排查会话激活异常、并发策略不生效等问题。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | [in] 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *session | [in] 指向目标会话管理器实例的指针，用于打印快照信息。 |
| int32_t fd | [in] 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回值：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | <ul> <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li> <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager或session为空指针。</li> </ul> |


