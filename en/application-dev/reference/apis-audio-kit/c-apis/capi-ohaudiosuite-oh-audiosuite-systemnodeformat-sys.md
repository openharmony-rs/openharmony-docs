# OH_AudioSuite_SystemNodeFormat(System API)

```c
typedef struct OH_AudioSuite_SystemNodeFormat {...} OH_AudioSuite_SystemNodeFormat
```

## Overview

Define the audio format info structure, used to describe basic audio format for system node.

<!--Device-struct OH_AudioSuite_SystemNodeFormat {...}--><!--Device-struct OH_AudioSuite_SystemNodeFormat {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.SuiteEngine

**Since**: 26.0.0

**System API:** This is a system API.

**Related module**: [OHAudioSuite](capi-audio-kit-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h(System API)](capi-native-audio-suite-base-h-sys.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Audio sampling rate.<br>**Since**: 26.0.0<br><!--Device-OH_Audio_SampleRate samplingRate--><!--Device-OH_Audio_SampleRate samplingRate-End--> |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.<br>**Since**: 26.0.0<br><!--Device-OH_AudioChannelLayout channelLayout--><!--Device-OH_AudioChannelLayout channelLayout-End--> |
| uint32_t channelCount | Audio channel count.<br>**Since**: 26.0.0<br><!--Device-uint32_t channelCount--><!--Device-uint32_t channelCount-End--> |
| int32_t encoding | Audio encoding format.<br>**Since**: 26.0.0<br><!--Device-int32_t encoding--><!--Device-int32_t encoding-End--> |
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Audio sample format.<br>**Since**: 26.0.0<br><!--Device-OH_Audio_SampleFormat sampleFormat--><!--Device-OH_Audio_SampleFormat sampleFormat-End--> |


