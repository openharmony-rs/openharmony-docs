# native_audio_debugging_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @boxwall-->
<!--Designer: @magekkkk-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频快照管理器相关的接口，用于获取音频运行时快照信息。

**引用文件：** <ohaudio/native_audio_debugging_manager.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) | OH_AudioDebuggingManager | 声明音频快照管理器。用于获取音频运行时快照信息。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager** manager)](#oh_audiomanager_getaudiodebuggingmanager) | 获取音频快照管理器实例（单例）。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager* manager, int32_t fd)](#oh_audiodebuggingmanager_printappinfo) | 打印当前进程中所有音频模块的快照信息。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager* manager, OH_AudioRenderer* renderer, int32_t fd)](#oh_audiodebuggingmanager_printrendererinfo) | 打印指定音频播放实例的快照信息。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager* manager, OH_AudioCapturer* capturer, int32_t fd)](#oh_audiodebuggingmanager_printcapturerinfo) | 打印指定录音实例的快照信息。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager* manager, OH_AudioSessionManager* session, int32_t fd)](#oh_audiodebuggingmanager_printsessioninfo) | 打印指定会话管理器实例的快照信息。 |

## 函数说明

### OH_AudioManager_GetAudioDebuggingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)
```

**描述**

获取音频快照管理器实例（单例）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md)** manager | 输出参数，用于接收OH_AudioDebuggingManager实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr。 |

### OH_AudioDebuggingManager_PrintAppInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)
```

**描述**

打印当前进程中所有音频模块的快照信息。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md)* manager | 音频快照管理器实例，通过[OH_AudioManager_GetAudioDebuggingManager](#oh_audiomanager_getaudiodebuggingmanager)获取。 |
| int32_t fd | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr。 |

### OH_AudioDebuggingManager_PrintRendererInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(
    OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)
```

**描述**

打印指定音频播放实例的快照信息。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md)* manager | 音频快照管理器实例，通过[OH_AudioManager_GetAudioDebuggingManager](#oh_audiomanager_getaudiodebuggingmanager)获取。 |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md)* renderer | 目标音频播放实例指针。 |
| int32_t fd | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr，或参数renderer为nullptr。 |

### OH_AudioDebuggingManager_PrintCapturerInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(
    OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)
```

**描述**

打印指定录音实例的快照信息。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md)* manager | 音频快照管理器实例，通过[OH_AudioManager_GetAudioDebuggingManager](#oh_audiomanager_getaudiodebuggingmanager)获取。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md)* capturer | 目标录音实例指针。 |
| int32_t fd | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr，或参数capturer为nullptr。 |

### OH_AudioDebuggingManager_PrintSessionInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(
    OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)
```

**描述**

打印指定会话管理器实例的快照信息。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md)* manager | 音频快照管理器实例，通过[OH_AudioManager_GetAudioDebuggingManager](#oh_audiomanager_getaudiodebuggingmanager)获取。 |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md)* session | 目标会话管理器实例指针。 |
| int32_t fd | 文件描述符。小于0或不可写时输出到运行日志；否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| [OH_AudioCommon_Result](capi-native-audio-common-h.md#oh_audiocommon_result) | AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。<br>         AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr，或参数session为nullptr。 |
