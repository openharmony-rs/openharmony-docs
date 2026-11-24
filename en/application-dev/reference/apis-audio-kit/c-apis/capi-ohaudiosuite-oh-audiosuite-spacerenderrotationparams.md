# OH_AudioSuite_SpaceRenderRotationParams

```c
typedef struct OH_AudioSuite_SpaceRenderRotationParams {...} OH_AudioSuite_SpaceRenderRotationParams
```

## Overview

Space rendering dynamic mode parameters.

<!--Device-struct OH_AudioSuite_SpaceRenderRotationParams {...}--><!--Device-struct OH_AudioSuite_SpaceRenderRotationParams {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float x | X coordinate in space, value range: [-5.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23<br><!--Device-float x--><!--Device-float x-End--> |
| float y | Y coordinate in space, value range: [-5.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23<br><!--Device-float y--><!--Device-float y-End--> |
| float z | Z coordinate in space, value range: [-5.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23<br><!--Device-float z--><!--Device-float z-End--> |
| int32_t surroundTime | Single-week circumnavigation time, value range: [2, 40], unit: seconds. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23<br><!--Device-int32_t surroundTime--><!--Device-int32_t surroundTime-End--> |
| [OH_AudioSuite_SurroundDirection](capi-native-audio-suite-base-h.md#oh_audiosuite_surrounddirection) surroundDirection | Single-week circumnavigation direction.<br>**Since**: 23<br><!--Device-OH_AudioSuite_SurroundDirection surroundDirection--><!--Device-OH_AudioSuite_SurroundDirection surroundDirection-End--> |


