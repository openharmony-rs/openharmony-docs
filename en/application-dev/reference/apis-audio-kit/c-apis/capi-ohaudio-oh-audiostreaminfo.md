# OH_AudioStreamInfo

```c
typedef struct OH_AudioStreamInfo {...} OH_AudioStreamInfo
```

## Overview

Define the audio stream info structure, used to describe basic audio format.

<!--Device-struct OH_AudioStreamInfo {...}--><!--Device-struct OH_AudioStreamInfo {...}-End-->

**System capability**: SystemCapability.Multimedia.Audio.Core

**Since**: 19

**Related module**: [OHAudio](capi-audio-kit-ohaudio.md)

**Header file**: [native_audiostream_base.h](capi-native-audiostream-base-h.md)

## Summary

### Member variables

| Name | Description |
| -- | -- |
| int32_t samplingRate | Audio sampling rate.<br>**Since**: 19 |
| [OH_AudioChannelLayout](../../apis-avcodec-kit/c-apis/capi-native-audio-channel-layout-h.md#oh_audiochannellayout) channelLayout | Audio channel layout.<br>**Since**: 19 |
| [OH_AudioStream_EncodingType](capi-native-audiostream-base-h.md#oh_audiostream_encodingtype) encodingType | Audio encoding format type.<br>**Since**: 19 |
| [OH_AudioStream_SampleFormat](capi-native-audiostream-base-h.md#oh_audiostream_sampleformat) sampleFormat | Audio sample format.<br>**Since**: 19 |


