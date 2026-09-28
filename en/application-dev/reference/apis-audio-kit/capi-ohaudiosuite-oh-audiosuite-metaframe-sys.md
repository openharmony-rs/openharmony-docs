# OH_AudioSuite_MetaFrame (System API)

<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=b9233046c3f90e6ca45044fd6224c6d08e2aa256 translatedAt=2026-08-31T02:33:26.210Z pushedAt=2026-08-31T08:31:46.984Z -->

```c
typedef struct OH_AudioSuite_MetaFrame {...} OH_AudioSuite_MetaFrame
```

## Overview

Defines a frame structure that contains audio data and metadata.

**Since:** 26.0.0

**System API:** This is a system API.

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

**Header File:** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| void* audioData | Pointer to the audio data. |
| int32_t audioDataSize | Size of the audio data. |
| void* metaData | Pointer to the metadata. |
| int32_t metaDataSize | Size of the metadata. |