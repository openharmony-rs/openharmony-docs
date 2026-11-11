# OH_AudioSuite_SpaceRenderRotationParams
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=06452fd8408a96522ed49232898af3be987bffbc translatedAt=2026-11-03T04:28:10.746Z pushedAt=2026-11-04T03:11:47.038Z nl=1 -->

```c
typedef struct OH_AudioSuite_SpaceRenderRotationParams {...} OH_AudioSuite_SpaceRenderRotationParams
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
| [OH_AudioSuite_SurroundDirection](capi-native-audio-suite-base-h.md#oh_audiosuite_surrounddirection) surroundDirection | Surround direction. 0 indicates counterclockwise rotation, and 1 indicates clockwise rotation. |