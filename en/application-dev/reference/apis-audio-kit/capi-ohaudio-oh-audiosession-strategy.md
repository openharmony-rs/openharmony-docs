# OH_AudioSession_Strategy
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @funny_sunix-->
<!--Designer: @hao-liangfei-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b22c6674b708ae694f3788c548df7cae0dc22384 translatedAt=2026-11-03T04:22:02.845Z pushedAt=2026-11-04T03:11:47.009Z nl=1 -->

```c
typedef struct OH_AudioSession_Strategy {...} OH_AudioSession_Strategy;
```

## Overview

The struct describes an audio session strategy.

Since API version 24, this struct is moved from **native_audio_session_manager.h** to **native_audio_session_base.h**.

Before API version 24, reference **native_audio_session_manager.h** to use this struct. Since API version 24, you can reference either **native_audio_session_manager.h** or **native_audio_session_base.h** to use this struct.

**Since**: 12

**Related module**: [OHAudio](capi-ohaudio.md)

**File to include:** [native_audio_session_base.h](capi-native-audio-session-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_AudioSession_ConcurrencyMode](capi-native-audio-session-base-h.md#oh_audiosession_concurrencymode) concurrencyMode | Audio concurrency mode.|


