# OH_AudioFormat

```c
typedef struct OH_AudioFormat {...} OH_AudioFormat
```

## Overview

Define the audio format info structure, used to describe basic audio format.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Audio sampling rate.<br>**Since**: 22 |
| OH_AudioChannelLayout channelLayout | Audio channel layout.<br>**Since**: 22 |
| uint32_t channelCount | Audio channel count.<br>**Since**: 22 |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | Audio encoding format type.<br>**Since**: 22 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Audio sample format.<br>**Since**: 22 |


