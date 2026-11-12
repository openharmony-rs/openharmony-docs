# OH_AudioSuite_ConverterOutputInfo

```c
typedef struct OH_AudioSuite_ConverterOutputInfo {...} OH_AudioSuite_ConverterOutputInfo
```

## Overview

Defines the output data structure of the audio converter, which is used to receive the converted audio data in direct processing mode.

<!--Device-struct OH_AudioSuite_ConverterOutputInfo {...}--><!--Device-struct OH_AudioSuite_ConverterOutputInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.1.0

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_converter.h](capi-native-audio-converter-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| void *data | Pointer to the buffer of the output audio data, which is allocated by the caller. Conversion results will be written to this buffer. The specific data type is determined by the sampling format [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat). Must remain valid during a call to [OH_AudioSuite_ConverterDirectProcess](capi-native-audio-converter-h.md#oh_audiosuite_converterdirectprocess). The value cannot be NULL.<br>**Since**: 26.1.0 |
| uint32_t size | Size of the output buffer, in bytes. The value must be greater than 0.<br>**Since**: 26.1.0 |
| uint32_t writeSize | Output parameter, which returns the number of bytes actually written to the output buffer. No initialization is required before invoking. No content is written when the call fails.<br>**Since**: 26.1.0 |


