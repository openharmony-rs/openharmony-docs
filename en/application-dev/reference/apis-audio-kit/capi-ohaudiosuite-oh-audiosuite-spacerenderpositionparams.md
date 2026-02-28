# OH_AudioSuite_SpaceRenderPositionParams
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AudioSuite_SpaceRenderPositionParams
```

## Overview

Defines configuration parameters for the fixed positioning mode of effect nodes in 3D spatial rendering.<br>Left-handed coordinate system: Extend your left hand and form an "L" shape with your thumb and index finger. Point your thumb to the right, index finger upward, and the remaining fingers forward. This forms a 3D left-handed coordinate system, where the thumb, index finger, and remaining fingers represent the positive directions of the x-axis, y-axis, and z-axis, respectively.

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
