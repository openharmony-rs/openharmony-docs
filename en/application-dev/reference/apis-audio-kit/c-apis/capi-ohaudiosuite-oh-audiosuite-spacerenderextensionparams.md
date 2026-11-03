# OH_AudioSuite_SpaceRenderExtensionParams

```c
struct OH_AudioSuite_SpaceRenderExtensionParams {...}
```

## Overview

Space rendering extension mode parameters.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 23

**Related module**: [OHAudioSuite](capi-others-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| float extRadius | Expansion radius, value range: [1.0, 5.0], unit: meters. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |
| int32_t extAngle | Expansion angle, value range: (0, 360), unit: degrees. If the value is out of range, the setting will fail and return [AUDIOSUITE_ERROR_INVALID_PARAM](capi-native-audio-suite-base-h.md#oh_audiosuite_result).<br>**Since**: 23 |


