# OH_AudioSession_Strategy
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct OH_AudioSession_Strategy {...} OH_AudioSession_Strategy
```

## Overview

The struct describes an audio session strategy.

Since API version 24, this struct has been moved from **native_audio_session_manager.h** to **native_audio_session_base.h**.

Before API version 24, use this struct only when **native_audio_session_manager.h** is referenced. Since API version 24, this struct can be used as long as **native_audio_session_manager.h** or **native_audio_session_base.h** is referenced.

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_session_base.h](capi-native-audio-session-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AudioSession_ConcurrencyMode](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) concurrencyMode | Audio concurrency mode.|
