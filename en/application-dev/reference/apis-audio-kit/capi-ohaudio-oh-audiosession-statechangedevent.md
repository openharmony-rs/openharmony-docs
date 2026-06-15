# OH_AudioSession_StateChangedEvent
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

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
| [OH_AudioSession_StateChangeHint](capi-native-audio-session-manager-h.md#oh_audiosession_statechangehint) stateChangeHint | Reason for deactivating the audio session.|
