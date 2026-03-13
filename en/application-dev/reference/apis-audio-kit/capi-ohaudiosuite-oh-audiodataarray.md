# OH_AudioDataArray
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AudioDataArray
```

## Overview

The struct describes the input data for the multi-output rendering interface. It is used to obtain processed audio data when multiple output effect nodes are present in the pipeline.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| void **audioDataArray | Double pointer to the addresses of the audio data to be output.|
| int32_t arraySize | Size of the audio data array.|
| int32_t requestFrameSize | Memory size (in bytes) allocated for each address in **audioDataArray**. Ensure that each address has sufficient memory allocated as specified by **requestFrameSize**.|
