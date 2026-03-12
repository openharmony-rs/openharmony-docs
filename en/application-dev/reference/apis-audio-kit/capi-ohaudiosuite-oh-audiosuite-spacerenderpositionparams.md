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

Defines the configuration parameters of the 3D spatial rendering effect node in fixed placement mode.<br>Left-handed coordinate system: Extend your left hand and form an "L" shape with your thumb and index finger. The thumb points to the right, the index finger points upward, and the other fingers point forward. This creates a 3D left-handed coordinate system. In this coordinate system, the thumb, index finger, and other fingers represent the positive directions of the x-axis, y-axis, and z-axis, respectively.

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
