# OH_AudioAccessoryNoiseReductionCapability

```c
typedef struct OH_AudioAccessoryNoiseReductionCapability {...} OH_AudioAccessoryNoiseReductionCapability
```

## Overview

Defines the noise reduction capability of an audio accessory.

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of this structure in bytes. Must be initialized by the caller (e.g., info.structSize = sizeof(OH_AudioAccessoryNoiseReductionCapability)). The framework uses this to determine which version of the structure is being used.<br>**Since**: 26.0.0 |
| const OH_AudioNoiseReductionMode *supportedModes | Array of supported noise reduction modes.<br>**Since**: 26.0.0 |
| uint32_t supportedModeCount | Number of supported noise reduction modes.<br>**Since**: 26.0.0 |
| OH_AudioNoiseReductionMode currentMode | The current noise reduction mode of the device. This represents the initial state when the capability is registered.<br>**Since**: 26.0.0 |


