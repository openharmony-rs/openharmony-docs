# OH_AudioSession_DeactivatedEvent

```c
struct OH_AudioSession_DeactivatedEvent {...}
```

## 概述

定义音频会话已停用事件结构体， 该结构体用于在[OH_AudioSession_DeactivatedCallback](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedcallback) 回调函数内传递会话停用事件的详细信息。

**系统能力：** SystemCapability.Multimedia.Audio.Core

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_session_manager.h](capi-native-audio-session-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AudioSession_DeactivatedReason](capi-native-audio-session-manager-h.md#oh_audiosession_deactivatedreason) reason | 音频会话停用原因。 |


