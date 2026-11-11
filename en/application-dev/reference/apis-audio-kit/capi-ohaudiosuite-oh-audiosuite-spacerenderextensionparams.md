# OH_AudioSuite_SpaceRenderExtensionParams
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @xxngwang-->
<!--Designer: @jay-liusong-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->
<!-- md-trans-meta sourceCommit=e9ec8701c87cf0327fd7aa17be40e1c4aeed0156 translatedAt=2026-11-10T03:09:35.184Z pushedAt=2026-11-10T04:48:16.632Z nl=1 -->

```c
struct OH_AudioSuite_SpaceRenderExtensionParams {...} OH_AudioSuite_SpaceRenderExtensionParams
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
| float extRadius | Extension radius, which indicates the spatial diffusion range of the sound source. A larger value indicates a wider spatial diffusion range of the sound. The value ranges from [1.0, 5.0], in meters (m). |
| int32_t extAngle | Extension angle, which indicates the diffusion angle range of the sound source on the horizontal plane. A larger value indicates a wider diffusion angle of the sound. The value ranges from (0, 360), in degrees (°). |


