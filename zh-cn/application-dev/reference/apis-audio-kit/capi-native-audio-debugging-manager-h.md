# native_audio_debugging_manager.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @zhanganxiang1-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频调试管理器相关的接口。本文件中的接口用于获取音频调试管理器实例，提供音频运行时调试功能，包括快照信息获取等。

**引用文件：** <ohaudio/native_audio_debugging_manager.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) | OH_AudioDebuggingManager | 声明音频调试管理器。用于音频运行时调试，包括获取快照信息等功能。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)](#oh_audiomanager_getaudiodebuggingmanager) | 获取音频调试管理器实例（单例）。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)](#oh_audiodebuggingmanager_printappinfo) | 打印当前进程中所有音频模块的快照信息。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)](#oh_audiodebuggingmanager_printrendererinfo) | 打印指定音频播放实例的快照信息。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)](#oh_audiodebuggingmanager_printcapturerinfo) | 打印指定录音实例的快照信息。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)](#oh_audiodebuggingmanager_printsessioninfo) | 打印指定会话管理器实例的快照信息。 |

## 函数说明

### OH_AudioManager_GetAudioDebuggingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)
```

**描述**

获取音频调试管理器实例（单例）。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) **manager | 输出参数，用于接收OH_AudioDebuggingManager实例。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr。</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintAppInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)
```

**描述**

打印当前进程中所有音频模块的快照信息。

> **说明：** 
> 
> 快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| int32_t fd | 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager为nullptr。</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintRendererInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)
```

**描述**

打印指定音频播放实例的快照信息。

> **说明：** 
> 
> 快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| OH_AudioRenderer *renderer | 指向目标音频播放实例的指针，用于打印快照信息。 |
| int32_t fd | 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager或renderer为nullptr。</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintCapturerInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)
```

**描述**

打印指定录音实例的快照信息。

> **说明：** 
> 
> 快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| OH_AudioCapturer *capturer | 指向目标录音实例的指针，用于打印快照信息。 |
| int32_t fd | 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager或capturer为nullptr。</li><br>         </ul> |

### OH_AudioDebuggingManager_PrintSessionInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)
```

**描述**

打印指定会话管理器实例的快照信息。

> **说明：** 
> 
> 快照信息的内容和格式随版本迭代发生变化，仅供人工调试参考，不建议开发者依据快照信息开发功能逻辑。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | 通过[OH_AudioManager_GetAudioDebuggingManager](capi-native-audio-debugging-manager-h.md#oh_audiomanager_getaudiodebuggingmanager)获取的音频调试管理器实例。 |
| [OH_AudioSessionManager](capi-ohaudio-oh-audiosessionmanager.md) *session | 指向目标会话管理器实例的指针，用于打印快照信息。 |
| int32_t fd | 文件描述符。当fd小于0或不可写时，快照信息将输出到运行日志，否则输出到fd指向的文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | <ul><br>         <li>AUDIOCOMMON_RESULT_SUCCESS：函数执行成功。</li><br>         <li>AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM：参数manager或session为nullptr。</li><br>         </ul> |


