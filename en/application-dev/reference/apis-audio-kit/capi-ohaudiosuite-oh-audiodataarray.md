# OH_AudioDataArray
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e9ec8701c87cf0327fd7aa17be40e1c4aeed0156 translatedAt=2026-11-10T03:08:41.802Z pushedAt=2026-11-10T04:47:29.872Z nl=1 -->

```c
typedef struct OH_AudioDataArray {...} OH_AudioDataArray
```

## Overview

Defines the output data description of the multi-output rendering interface. When there are multiple output effect nodes in the pipeline, the processed audio data is obtained through the multi-output rendering interface.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void **audioDataArray | Address of the output audio data. |
| int32_t arraySize | Number of elements in the audioDataArray array. |
| int32_t requestFrameSize | Size of the memory pointed to by each address in the audioDataArray array, in bytes. Ensure that the size of the memory pointed to by each address complies with the requestFrameSize field definition. |


