# OH_AudioSession_StateChangedEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @LauJianghu-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=384124d51e7a0d80d857fbba0b4adc75a16563d8 translatedAt=2026-11-03T04:21:57.318Z pushedAt=2026-11-04T03:11:47.003Z nl=1 -->

```c
typedef struct OH_AudioSession_StateChangedEvent {...} OH_AudioSession_StateChangedEvent
```
## Overview

The struct describes the event indicating that the audio session state changes.

**Since**: 20

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_session_manager.h](capi-native-audio-session-manager-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) stateChangeHint | Audio session state change hint, which indicates the type of state change, such as mute, unmute, pause, and resume. |


