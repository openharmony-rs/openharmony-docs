# OH_AudioFormat
<!--Kit: Audio Kit-->
<!--Subsystem: Multimedia-->
<!--Owner: @songshenke-->
<!--Designer: @caixuejiang; @hao-liangfei; @zhanganxiang-->
<!--Tester: @Filger-->
<!--Adviser: @w_Machine_cc-->

```c
typedef struct {...} OH_AudioFormat
```

## Overview

The struct describes the audio stream information, which is used to describe the basic audio format, required for audio creation.

**Since**: 22

**Related module**: [OHAudioSuite](capi-ohaudiosuite.md)

**Header file**: [native_audio_suite_base.h](capi-native-audio-suite-base-h.md)

## Summary

### Member Variables

| Name| Description|
| -- | -- |
| [OH_Audio_SampleRate](capi-native-audio-suite-base-h.md#oh_audio_samplerate) samplingRate | Sample rate of the audio stream.|
| OH_AudioChannelLayout channelLayout | Channel layout of the audio stream. Currently, only **CH_LAYOUT_MONO** and **CH_LAYOUT_STEREO** are supported.|
| uint32_t channelCount | Number of audio channels in the audio stream. Currently, only single-channel (1) and dual-channel (2) configurations are supported.|
| [OH_Audio_EncodingType](capi-native-audio-suite-base-h.md#oh_audio_encodingtype) encodingType | Encoding type used for the audio stream.|
| [OH_Audio_SampleFormat](capi-native-audio-suite-base-h.md#oh_audio_sampleformat) sampleFormat | Sample format of the audio stream.|
