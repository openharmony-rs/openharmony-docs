# OH_AudioFormat

```c
typedef struct OH_AudioFormat {...} OH_AudioFormat
```

## Overview

Define the audio format info structure, used to describe basic audio format.

<!--Device-struct OH_AudioFormat {...}--><!--Device-struct OH_AudioFormat {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 22

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Audio sampling rate.<br>**Since**: 22 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.<br>**Since**: 22 |
| uint32_t channelCount | Audio channel count.<br>**Since**: 22 |
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | Audio encoding format type.<br>**Since**: 22 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Audio sample format.<br>**Since**: 22 |


