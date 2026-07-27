# OH_AudioSuite_SpaceRenderExtensionParams
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
struct OH_AudioSuite_SpaceRenderExtensionParams {...}
```

## Overview

Defines the configuration parameters of the spatial rendering effect node in extension mode.

**Since**: 23

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| float extRadius | Extension radius. The value range is [1.0, 5.0], in meters.|
| int32_t extAngle | Extension angle. The value range is (0, 360), in degrees.|
