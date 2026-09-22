# OH_AudioAccessoryCapabilities

```c
typedef struct OH_AudioAccessoryCapabilities {...} OH_AudioAccessoryCapabilities
```

## Overview

Defines the capabilities of an audio accessory.<br> <b>Version Control:</b> Callers MUST set structSize to sizeof(OH_AudioAccessoryCapabilities).

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 26.0.0

**Related module**: [OHAudio](capi-ohaudio.md)

**Header file**: [native_audio_accessory_common.h](capi-native-audio-accessory-common-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| uint32_t structSize | Size of this structure in bytes. Must be initialized by the caller (e.g., caps.structSize = sizeof(OH_AudioAccessoryCapabilities)).<br>**Since**: 26.0.0 |
| const OH_AudioStreamInfo *streamProperties | Array of supported stream configurations. Each entry represents one valid combination of sample rate, format, and channel count. The framework performs a deep copy of this array.<br>**Since**: 26.0.0 |
| uint32_t streamPropertyCount | Number of supported stream configurations.<br>**Since**: 26.0.0 |


