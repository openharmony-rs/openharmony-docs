# OH_AudioSuite_SpaceRenderRotationParams
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AudioSuite_SpaceRenderRotationParams
```

## Overview

Defines the configuration parameters of the spatial rendering effect node in rotation mode.

**Since**: 23

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float x | X coordinate in the space. The value range is [-5.0, 5.0], in meters.|
| float y | Y coordinate in the space. The value range is [-5.0, 5.0], in meters.|
| float z | Z coordinate in the space. The value range is [-5.0, 5.0], in meters.|
| int32_t surroundTime | Single-cycle rotation time. The value range is [2, 40], in seconds.|
| [OH_AudioSuite_SurroundDirection](capi-native-audio-suite-base-h.md#oh_audiosuite_surrounddirection) surroundDirection | Single-cycle rotation direction. The value range is [0,1].|
