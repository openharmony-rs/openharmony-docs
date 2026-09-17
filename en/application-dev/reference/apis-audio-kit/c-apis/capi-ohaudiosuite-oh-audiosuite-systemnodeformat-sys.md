# OH_AudioSuite_SystemNodeFormat(System API)

```c
typedef struct OH_AudioSuite_SystemNodeFormat {...} OH_AudioSuite_SystemNodeFormat
```

## Overview

Define the audio format info structure, used to describe basic audio format for system node.

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h(System API)](capi-native-audio-suite-base-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Audio sampling rate.<br>**Since**: 26.0.0 |
| OH_AudioChannelLayout channelLayout | Audio channel layout.<br>**Since**: 26.0.0 |
| uint32_t channelCount | Audio channel count.<br>**Since**: 26.0.0 |
| int32_t encoding | Audio encoding format.<br>**Since**: 26.0.0 |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Audio sample format.<br>**Since**: 26.0.0 |


