# OH_AudioSuite_SpaceRenderRotationParams

```c
struct OH_AudioSuite_SpaceRenderRotationParams {...}
```

## Overview

Space rendering dynamic mode parameters.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

**Related module**: [OHAudioSuite](capi-others-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float x | X coordinate in space, value range: [-5.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |
| float y | Y coordinate in space, value range: [-5.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |
| float z | Z coordinate in space, value range: [-5.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |
| int32_t surroundTime | Single-week circumnavigation time, value range: [2, 40], unit: seconds. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |
| [OH_AudioSuite_SurroundDirection](capi-native-audio-suite-base-h.md#oh_audiosuite_surrounddirection) surroundDirection | Single-week circumnavigation direction.<br>**Since**: 23 |


