# OH_AudioSession_StateChangedEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @LauJianghu-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSession_StateChangedEvent {...} OH_AudioSession_StateChangedEvent
```
## 概述

音频会话状态变更事件。

**起始版本：** 20

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_session_manager.h](capi-native-audio-session-manager-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) stateChangeHint | 音频会话状态变更提示，用于表示状态变化的类型，如静音、取消静音、暂停、恢复等。 |


