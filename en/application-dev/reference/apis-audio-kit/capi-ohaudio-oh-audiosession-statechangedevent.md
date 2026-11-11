# OH_AudioSession_StateChangedEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @LauJianghu-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=df323590568bcaa8e37154b055d996f5d882aa3b translatedAt=2026-11-10T03:07:41.885Z pushedAt=2026-11-10T04:47:14.652Z nl=1 -->

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


