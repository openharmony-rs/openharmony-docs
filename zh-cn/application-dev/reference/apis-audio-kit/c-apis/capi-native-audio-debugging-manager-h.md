# native_audio_debugging_manager.h

## 概述

Declare audio debugging manager related interfaces.The interfaces in this file are used for audio debugging, helping the developers toanalyze issues when implementing audio related functions more efficiently.

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 26.0.0

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) | OH_AudioDebuggingManager | 声明音频调试管理器。音频调试管理器为开发者提供了很多功能，可以通过音频系统运行时信息。 |

### 函数

| 名称 | 描述 |
| -- | -- |
| [OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)](#oh_audiomanager_getaudiodebuggingmanager) | 获取音频调试管理器句柄，它是一个单例。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)](#oh_audiodebuggingmanager_printappinfo) | 打印当前应用进程的完整音频运行时快照。快照将包含所有音频渲染器、捕获器、音频会话信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)](#oh_audiodebuggingmanager_printrendererinfo) | 打印目标音频渲染器实例的完整音频运行时快照。快照将包含流、管道、卷和设备信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)](#oh_audiodebuggingmanager_printcapturerinfo) | 打印目标音频捕获程序实例的完整音频运行时快照。快照将包含流、管道、卷和设备信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。 |
| [OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)](#oh_audiodebuggingmanager_printsessioninfo) | 打印目标音频会话管理器实例的完整音频运行时快照。快照将包含会话状态、场景、策略和设备信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。 |

## 函数说明

### OH_AudioManager_GetAudioDebuggingManager()

```c
OH_AudioCommon_Result OH_AudioManager_GetAudioDebuggingManager(OH_AudioDebuggingManager **manager)
```

**描述**

获取音频调试管理器句柄，它是一个单例。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) **manager | 获取{@link OH_AudioDebugManager}实例的输出参数。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | 如果执行成功，则返回[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)。<br> [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)管理器的参数为nullptr。 |

### OH_AudioDebuggingManager_PrintAppInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintAppInfo(OH_AudioDebuggingManager *manager, int32_t fd)
```

**描述**

打印当前应用进程的完整音频运行时快照。快照将包含所有音频渲染器、捕获器、音频会话信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | {@link OH_AudioManager_GetAudioDebugsManager}提供的{@link OH_AudioDebugsManager}句柄。 |
| int32_t fd | 是一个文件描述符，表示快照信息将要写入的位置。如果fd小于0或者不可写，则会将快照信息打印到运行日志中。否则快照将写入文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | 如果执行成功，则返回[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)。<br> [AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM](capi-native-audio-common-h.md#oh_audiocommon_result)管理器的参数为nullptr。 |

### OH_AudioDebuggingManager_PrintRendererInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintRendererInfo(OH_AudioDebuggingManager *manager, OH_AudioRenderer *renderer, int32_t fd)
```

**描述**

打印目标音频渲染器实例的完整音频运行时快照。快照将包含流、管道、卷和设备信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | {@link OH_AudioManager_GetAudioDebugsManager}提供的{@link OH_AudioDebugsManager}句柄。 |
| [OH_AudioRenderer](capi-ohaudio-oh-audiorendererstruct.md) *renderer | 指向要打印快照的目标音频渲染器实例的指针。 |
| int32_t fd | 是一个文件描述符，表示快照信息将要写入的位置。如果fd小于0或者不可写，则会将快照信息打印到运行日志中。否则快照将写入文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | 如果执行成功，则返回[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)。<br> {@链接AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} 1.管理器的参数为nullptr；<br> 2.渲染器的param为nullptr； |

### OH_AudioDebuggingManager_PrintCapturerInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintCapturerInfo(OH_AudioDebuggingManager *manager, OH_AudioCapturer *capturer, int32_t fd)
```

**描述**

打印目标音频捕获程序实例的完整音频运行时快照。快照将包含流、管道、卷和设备信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | {@link OH_AudioManager_GetAudioDebugsManager}提供的{@link OH_AudioDebugsManager}句柄。 |
| [OH_AudioCapturer](capi-ohaudio-oh-audiocapturerstruct.md) *capturer | 指向要打印快照的目标音频捕获器实例的指针。 |
| int32_t fd | 是一个文件描述符，表示快照信息将要写入的位置。如果fd小于0或者不可写，则会将快照信息打印到运行日志中。否则快照将写入文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | 如果执行成功，则返回[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)。<br> {@链接AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} 1.管理器的参数为nullptr；<br> 2.捕获器的参数为nullptr； |

### OH_AudioDebuggingManager_PrintSessionInfo()

```c
OH_AudioCommon_Result OH_AudioDebuggingManager_PrintSessionInfo(OH_AudioDebuggingManager *manager, OH_AudioSessionManager *session, int32_t fd)
```

**描述**

打印目标音频会话管理器实例的完整音频运行时快照。快照将包含会话状态、场景、策略和设备信息。请注意，不同版本的信息详情和格式可能会有所不同，它只能用于手动调试，用户不应依赖实际功能实现或文件的信息内容提取。

**起始版本：** 26.0.0

**参数：**

| 参数项 | 描述 |
| -- | -- |
| [OH_AudioDebuggingManager](capi-ohaudio-oh-audiodebuggingmanager.md) *manager | {@link OH_AudioManager_GetAudioDebugsManager}提供的{@link OH_AudioDebugsManager}句柄。 |
| OH_AudioSessionManager *session | 指向要打印快照的目标音频会话管理器实例的指针。 |
| int32_t fd | 是一个文件描述符，表示快照信息将要写入的位置。如果fd小于0或者不可写，则会将快照信息打印到运行日志中。否则快照将写入文件。 |

**返回：**

| 类型 | 说明 |
| -- | -- |
| OH_AudioCommon_Result | 如果执行成功，则返回[AUDIOCOMMON_RESULT_SUCCESS](capi-native-audio-common-h.md#oh_audiocommon_result)。<br> {@链接AUDIOCOMMON_RESULT_ERROR_INVALID_PARAM} 1.管理器的参数为nullptr；<br> 2.session的param为nullptr； |


