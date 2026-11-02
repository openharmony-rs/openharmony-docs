# OH_AudioSuite_SpaceRenderPositionParams

```c
struct OH_AudioSuite_SpaceRenderPositionParams {...}
```

## Overview

Definition of the parameter structure for fixed position mode in 3D spatial rendering. Left-hand coordinate system: Extend your left hand, forming an "L" shape with your thumb and index finger. Point the thumb to the right, the index finger upward, and the remaining fingers forward. This establishes a left-hand coordinate system. In this system, the thumb, index finger, and other fingers represent the positive directions of the x, y, and z axes, respectively.

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


