# OH_AudioSession_Strategy
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSession_Strategy {...} OH_AudioSession_Strategy;
```

## 概述

音频会话策略。

从API version 24开始，此结构体由native_audio_session_manager.h移动至native_audio_session_base.h文件。

在API version 24之前，使用该结构体请引用native_audio_session_manager.h头文件；从API version 24开始，引用native_audio_session_manager.h或native_audio_session_base.h均可正常使用该结构体。

**起始版本：** 12

**相关模块：** [OHAudio](capi-ohaudio.md)

**所在头文件：** [native_audio_session_base.h](capi-native-audio-session-base-h.md)

## 汇总

### 成员变量

| 名称 | 描述 |
| -- | -- |
| [OH_AudioSession_ConcurrencyMode](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) concurrencyMode | 音频并发模式。 |


