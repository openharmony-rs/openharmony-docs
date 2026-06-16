# native_audio_session_base.h
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

## 概述

声明音频会话基础数据结构。

**引用文件：** <ohaudio/native_audio_session_base.h>

**库：** libohaudio.so

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 24

**相关模块：** [OHAudio](capi-ohaudio.md)

## 汇总

### 结构体

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSession_Strategy](capi-ohaudio-oh-audiosession-strategy.md) | OH_AudioSession_Strategy | 音频会话策略。 |

### 枚举

| 名称 | typedef关键字 | 描述 |
| -- | -- | -- |
| [OH_AudioSession_BehaviorFlags](#oh_audiosession_behaviorflags) | OH_AudioSession_BehaviorFlags | 音频会话行为标志。 |
| [OH_AudioSession_ConcurrencyMode](#oh_audiosession_concurrencymode) | OH_AudioSession_ConcurrencyMode | 音频并发模式。 |

## 枚举类型说明

### OH_AudioSession_BehaviorFlags

```c
enum OH_AudioSession_BehaviorFlags
```

**描述**

音频会话行为标志。

**起始版本：** 24

| 枚举项 | 描述 |
| -- | -- |
| DEFAULT_BEHAVIOR = 0x00000000 | 默认行为，用于清除会话行为标记。<br>**起始版本：** 24 |
| VOIP_PRIVACY_TYPE_PUBLIC = 0x00000001 | 非隐私VoIP，允许被录音。允许VoIP录音流与其他应用的录音流共同录音。<br>**起始版本：** 26.0.0 |
| MUTE_WHEN_INTERRUPTED = 0x00000002 | 当系统需要停止或暂停音频流时，执行强制静音替代。<br>调用[OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior)接口配置该行为时，必须同步调用[OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene)接口，否则配置将无法生效。<br>在音频会话场景下，当音频流静音或恢复时，应用将分别收到[OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_MUTE与[OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_UNMUTE的通知。<br>在OH_AudioRenderer和OH_AudioCapturer场景下，当音频流静音或恢复时，应用将分别收到[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_MUTE与[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_UNMUTE的通知。<br/>**注意：** 该标志不能与PAUSE_WHEN_INTERRUPTED共存，若同时设置，仅PAUSE_WHEN_INTERRUPTED生效。<br>**起始版本：** 24 |
| PAUSE_WHEN_INTERRUPTED = 0x00000004 | 当系统需要停止音频流时，执行暂停替代。<br>调用[OH_AudioSessionManager_SetBehavior](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setbehavior)接口配置该行为时，必须同步调用[OH_AudioSessionManager_SetScene](capi-native-audio-session-manager-h.md#oh_audiosessionmanager_setscene)接口，否则配置将无法生效。<br>在音频会话场景下，当音频流暂停或恢复时，应用将分别收到[OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_PAUSE与[OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint).AUDIO_SESSION_STATE_CHANGE_HINT_RESUME的通知。<br>在OH_AudioRenderer和OH_AudioCapturer场景下，当音频流暂停或恢复时，应用将分别收到[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_PAUSE与[OH_AudioInterrupt_Hint](capi-native-audiostream-base-h.md#oh_audiointerrupt_hint).AUDIOSTREAM_INTERRUPT_HINT_RESUME的通知。<br/>**注意：** 该标志不能与MUTE_WHEN_INTERRUPTED共存，若同时设置，仅该标志生效。<br>**起始版本：** 26.0.0 |

### OH_AudioSession_ConcurrencyMode

```c
enum OH_AudioSession_ConcurrencyMode
```

**描述**

音频并发模式。

从API version 24开始，此枚举由native_audio_session_manager.h移动至此头文件。

在API version 24之前，使用该枚举请引用native_audio_session_manager.h头文件；从API version 24开始，引用native_audio_session_manager.h或native_audio_session_base.h均可正常使用该枚举。

**起始版本：** 12

| 枚举项 | 描述 |
| -- | -- |
| CONCURRENCY_DEFAULT = 0 | 默认使用系统策略。 |
| CONCURRENCY_MIX_WITH_OTHERS = 1 | 当前应用与其他应用混音播放。 |
| CONCURRENCY_DUCK_OTHERS = 2 | 当前应用播放时会压低其他正在播放的应用音量。 |
| CONCURRENCY_PAUSE_OTHERS = 3 | 当前应用播放时会暂停其他正在播放的应用。 |


