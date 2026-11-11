# OH_AudioSuite_MetaFrame (System API)
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=a306395a78cd7ac89b1bdc20446e826350df2c3a translatedAt=2026-11-03T04:26:17.778Z pushedAt=2026-11-04T03:11:47.029Z nl=1 -->

```c
typedef struct OH_AudioSuite_MetaFrame {...} OH_AudioSuite_MetaFrame
```

## Overview

Defines a frame structure that contains audio data and metadata.

**Since:** 26.0.0

**System Interface:** This is a system interface.

**Related module:** [OHAudioSuite](capi-ohaudiosuite.md)

**File to include:** [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name | Description |
| -- | -- |
| void* audioData | Pointer to the audio data. |
| int32_t audioDataSize | Size of the audio data. |
| void* metaData | Pointer to the metadata. |
| int32_t metaDataSize | Size of the metadata. |


