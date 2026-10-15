# OH_AudioSession_StateChangedEvent

```c
struct OH_AudioSession_StateChangedEvent {...}
```

## 概述

声明音频会话状态变更事件结构体， 该结构体用于在[OH_AudioSession_StateChangedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_statechangedcallback) 回调函数内传递会话状态变更事件的详细信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 20

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_session_manager.h](capi-native-audio-session-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) stateChangeHint | 音频会话状态变更提示信息。开发者需要根据提示采取相应的响应策略。 |


