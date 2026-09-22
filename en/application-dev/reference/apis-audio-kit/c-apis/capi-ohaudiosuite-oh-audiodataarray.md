# OH_AudioDataArray

```c
typedef struct OH_AudioDataArray {...} OH_AudioDataArray
```

## Overview

Define the audio data array structure. This structure is used to get the processed audio data after acquisition processing during multi-channel rendering.

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void **audioDataArray | Pointer to the array of audio data pointers.<br>**Since**: 22 |
| int32_t arraySize | Audio arraySize.<br>**Since**: 22 |
| int32_t requestFrameSize | The memory size pointed to by each address in the audioDataArray array, in bytes. It should be ensured that the memory size pointed to by each address is requestFrameSize bytes.<br>**Since**: 22 |


