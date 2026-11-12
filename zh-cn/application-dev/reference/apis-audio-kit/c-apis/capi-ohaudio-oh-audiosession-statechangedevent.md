# OH_AudioSession_StateChangedEvent

```c
typedef struct OH_AudioSession_StateChangedEvent {...} OH_AudioSession_StateChangedEvent
```

## 概述

声明音频会话状态变更事件结构体， 该结构体用于在[OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) 回调函数内传递会话状态变更事件的详细信息。

<!--Device-struct OH_AudioSession_StateChangedEvent {...}--><!--Device-struct OH_AudioSession_StateChangedEvent {...}-End-->

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**相关模块：** [OHAudio](capi-audio-kit-ohaudio.md)

**所在头文件：** [native_audio_session_manager.h](capi-native-audio-session-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) stateChangeHint | 音频会话状态变更提示，用于表示状态变化的类型，如静音、取消静音、暂停、恢复等。 |


