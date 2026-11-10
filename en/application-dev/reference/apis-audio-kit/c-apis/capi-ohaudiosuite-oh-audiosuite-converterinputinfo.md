# OH_AudioSuite_ConverterInputInfo

```c
struct OH_AudioSuite_ConverterInputInfo {...}
```

## Overview

Defines the input data structure of the audio converter.

<!--Device-struct OH_AudioSuite_ConverterInputInfo {...}--><!--Device-struct OH_AudioSuite_ConverterInputInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_converter.h](capi-native-audio-converter-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| const void *data | Pointer to the input audio data buffer, which points to the original audio data and is allocated by the caller. The specific data type is determined by the sampling format [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Must remain valid during a call to [OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess). The value cannot be NULL.<br>**Since**: 26.1.0 |
| uint32_t size | Indicates the size of the input buffer, in bytes. Must be greater than 0.<br>**Since**: 26.1.0 |


