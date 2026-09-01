# OH_AudioSuite_SystemNodeFormat (System API)

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b9233046c3f90e6ca45044fd6224c6d08e2aa256 translatedAt=2026-08-31T02:33:42.734Z pushedAt=2026-08-31T08:09:13.536Z -->

```c
typedef struct OH_AudioSuite_SystemNodeFormat {...} OH_AudioSuite_SystemNodeFormat
```

## Overview

Defines the basic audio format of a system node.

**Since:** 26.0.0

**System API:** This is a system API.

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

**File to include:** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Sampling rate of the audio stream. |
| OH_AudioChannelLayout channelLayout | Channel layout of the audio stream. |
| uint32_t channelCount | Number of channels in the audio stream. |
| int32_t encoding | Encoding type of the audio stream. The value is 1 or 9, where 1 indicates the PCM encoding format and 9 indicates mixed audio data of PCM and metadata. |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Sampling format of the audio stream. |