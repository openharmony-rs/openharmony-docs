# OH_AudioDataArray
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e9ec8701c87cf0327fd7aa17be40e1c4aeed0156 translatedAt=2026-11-09T10:26:49.155Z pushedAt=2026-11-09T11:30:38.159Z nl=1 -->

```c
typedef struct OH_AudioDataArray {...} OH_AudioDataArray
```

## Overview

Defines the output data description of the multi-channel output rendering API. When a multi-output effect node exists in the pipeline, the processed audio data is obtained through the multi-channel output rendering API.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void **audioDataArray | Address of the output audio data. |
| int32_t arraySize | Number of elements in the audioDataArray array. |
| int32_t requestFrameSize | Memory size pointed to by each address in the audioDataArray array, in bytes. Ensure that the memory size pointed to by each address complies with the requestFrameSize field definition.|


